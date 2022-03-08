# __Event Sourcing Architecture__
---------------------------------------------------

> ## Abstract 

**Event Sourcing Architecture** is generally used to tell us about how to store the data in an organized manner so that we don't lose any data in it. Event Sourcing Architecture is used in microservices to overcome the CRUD Technique from the system. They are mainly based on independent processes and synchronize with each other through the API(*Application Program Interface*). The current state system is dependent on each other whereas in the event Sourcing adopts an ecosystem that makes it simple to create and maintain apps as a whole system is divided into a set of smaller task which is independent of each other. This paper is going to tell us about the working of event sourcing architecture with some examples.

> ## Introduction   
#

In today's world, we are dependent on databases, and if data is not going to store precious sequential data it is difficult for us to check previous data. There are several ways to store the current state data but to store previous state data Event Sourcing is the best way to store the previous store data.

Event Sourcing is the technique for storing data to event store(*which is work as a database*) in __add only mode__. Event Sourcing stores every data in add(*append*) mode only and each data record is known as an event. All the records changes that have been made over an application's state will come to form original data.

All changes made are represented as an event and are linked to the **event log**. The current business environment can be created by replaying all events in the order in which they occur. System information is available at events. Since the event has already taken place, it is always referred to in the past tense (*by an action object in the past*).

In this paper, we will be working to understand the full explanation of Event Sourcing Architecture. An Event Sourcing Architecture is a way to store the previous data in the database of events.

> ## What is Event Sourcing Architecture
#


* This is a type of implementation of "Event-driven Architecture".
* The database is going to store all the state changes which are called events.
* In the database we only add events.
* Events can not be modified or deleted.
* The current state of the application can be computed by applying all the events and the result can be cached in the local memory.

Event Sourcing Architecture is stored data that can not be deleted from its database because it always appends the events. whenever we add, remove or update the data record it acts as an event, and events are only added to the event store.

I can explain Event Sourcing Architecture using the table of records.

| Sid           | Sname         | Amount |
| ------------- |:-------------:| ------:|
|1190           |Satyanand      | 400    |
|1280           |Shivanand      | 1000   |
|1150           |Abhay          | 700    |

If I add one record to it as an Aman who has sid as 1342 and amount 5000.

| Sid           | Sname         | Amount |
| ------------- |:-------------:| ------:|
|1190           |Satyanand      | 400    |
|1280           |Shivanand      | 1000   |
|1150           |Abhay          | 700    |
|1342           |Aman           | 5000   |

If I remove the record of Satyanand it will be no longer visible to us.

| Sid           | Sname         | Amount |
| ------------- |:-------------:| ------:|
|1280           |Shivanand      | 1000   |
|1150           |Abhay          | 700    |
|1342           |Aman           | 5000   |

If someone else comes and wants to know all the records of the table then he is not able to see the record of Satyanand so in this case Event Sourcing Architecture comes into play. Event Sourcing Architecture can store all the records. The same table will be stored in Event Sourcing Architecture with one more column which will tell us about status.

| Sid           | Sname         | Amount | Status  |
| ------------- |:-------------:| ------:| -------:|
|1190           |Satyanand      | 400    | Removed |
|1280           |Shivanand      | 1000   | Addded  |
|1150           |Abhay          | 700    | Addded  |
|1342           |Aman           | 5000   | Addded  |

The Event Sourcing Architecture is *immutable* data events and they are always anonymous. The event sourcing pattern forms the path to handling operation on the data. Events are always in the past tense. Events should always be created and not deleted or modified. we need to always have a strategy in mind because events are only added.
__Git__ is one of the best examples of Event Sourcing Architecture.


![](https://microservices.io/i/storingevents.png)

The above figure it is showing the Event Sourcing Architecture on the right side of it. The ordered service on the left side stores the data in each column. the order service on the right side store the data event in the event store and customer service is subscribed to the events show that it has updated its status.

> ## Advantage of Event Sourcing Architecture

#

* Event Sourcing Architecture makes us look into the business terms as compared to the traditional CRUD(Create, read, update and delete) based Approach.
* It makes replicating a production problem simpler.
* It acts as a natural audit log.
* It has easy scaling immutable data.
* If we want to know the application state at any point in time we can determine easily by looking into the logs. 
* Different services can subscribe for the update they are interested in and update their local cache of the data.
* Easier to integrate different systems as they communicate with each other in terms of events.

> ## When not using Event Sourcing Architecture

#
 
* When we are not interested in the previous state of the data.
* CRUD might be sufficient for user service in an E-commerce application.

> ## Conclusion 

#  

This paper shows an event sourcing architecture as a general study on its components and databases.
An event-driven architecture is most commonly used in a product-based ecosystem, as this model is much more reliable and scalable than its other different parts. Git is one of the greatest examples of this system.
But in conclusion, I can say event sourcing architecture is a much better choice for availability and resilience where are required.

> ## References

# 
1. Chris Richardson, Pattern: Event sourcing, Kong [microservices. io/patterns/data/event-sourcing](https://microservices.io/patterns/data/event-sourcing.html)
 
2. Martin Fowler,Event Sourcing [martinfowler.com](https://martinfowler.com/eaaDev/EventSourcing.html) retrieved: 12-12-2005

3. Event Sourcing [eventuate. io](https://eventuate.io/whyeventsourcing.html) 
