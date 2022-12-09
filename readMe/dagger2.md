# Dagger 2
- https://medium.com/@harivigneshjayapalan/dagger-2-for-android-beginners-introduction-be6580cb3edb
- https://medium.com/@harivigneshjayapalan/dagger-2-for-android-beginners-dagger-2-part-i-f2de5564ab25
- https://medium.com/@harivigneshjayapalan/dagger-2-for-android-beginners-dagger-2-part-ii-436c3e3aa15b
- https://medium.com/@harivigneshjayapalan/dagger-2-for-android-beginners-advanced-part-i-1e14fccf2cc8

## What is Dependency ?
- Let’s assume class Student and a class Library. Student class is depend on Library.
- Here Student is dependant and Library is dependency
```
class Student{

public Student( ){
Library lib = new Library();
lib.getBooks();
}
}
```
## Why Dependency is Bad ?
- Hard dependencies reduce the re-usability
- Hard dependencies make it hard for testing
- Hard dependencies hinders code maintainability when the project scales up

## Re-usability
- When classes and methods are loosely or not coupled or not dependant on many things, it’s reusable nature increases. Reusability is one of the core commandment of object-oriented programming.

## Testing
- For testing, you will mock certain objects. But if there are so many dependencies within the method or the class, it will be hard to test. If a java class creates an instance of another class via the new operator, then it cannot be used and tested independently from that class.

## Maintainability
- When your code cannot be tested properly and the components are not reusable and if your project continues to grow, it will be very difficult to maintain. Maintainability includes a lot of other factors, but as long as new developers in your team understands the system and makes the work of developers comfortable, you are good to go.

## Types of Dependencies
- Dependencies are of many types, the common ones are 
- Class dependency - In the above example Student class is dependent on Library class in it’s constructor
- Interface dependency - When one interface is dependent on other interfaces. Let’s consider an Interface Reading, which have methods readBook(). All student class will be dependent on the interface
- Method/field dependency - Whatever methods defined in a class and that method is dependent on other
- Direct and indirect dependency - Let’s consider, Student is dependent on Library and library is dependent on Book. Here, Student is indirectly dependent on Book class

## Dagger 2 annotation
- @Inject
- @Component
- @Module
- @PerActivity
- @Provide
- @Singleton

## @Inject Annotation
- First and the most important for DI is the@Inject annotation. Part of JSR-330 standard marks those dependencies which should be provided by Dependency Injection framework. 
- Constructor Injection — is used with class constructor 
- Field Injection — is used with the fields in the class 
- Method Injection — is used with the functions/methods 
- In other words, the@Inject annotation will tell the Dagger what all the dependencies needed to be transferred to the dependant. It’s like the field agents of the iron bank, negotiate with the house and fix the amount of loan that they can provide.

## @Component Annotation
- This annotation is used to build the interface which wires everything together. 
- In this place, we define from which modules (or other Components) we’re taking dependencies. 
- Also here is the place to define which graph dependencies should be visible publicly (can be injected) and where our component can inject objects. 
- @Component, in general, is a something like a bridge between @Module(Which we’ll be seeing later) and @Inject.
- In other words, @Component annotations are the agent who is in charge of approving and transferring the loan amount to the respective accounts in the iron bank.
```
    @Component
    interface BattleComponent {
    War getWar();
    Starks getStarks();
    Boltons getBoltons();
    }
```

## @Module
- In short, @Module annotation, marks the modules/classes. 
- For example, Let’s talk in Android. We can have a module called ContextModule and this module can provide ApplicationContext and Context dependencies to other classes. 
- So we need to mark the class ContextModule with @Module.

## @Provides
- In short, @Provides annotation marks the methods inside the modules, which provides the dependencies. 
- For example, in the same example above, we marked ContextModule with @Module and we need to mark methods which provide ApplicationContext and Context with @Provides.

## @PerActivity

## @PerFragment

- For more details follow below link
- https://github.com/Hariofspades/Dagger-2-Advanced/tree/InjectMainActivity




