# HowOldAreMyDependencies-maven-plugin

This plugin generates a report on how old your dependencies are (WORK IN PROGRESS)

## Usage
```
mvn howoldaremydependencies:generate-report
```

To invoke this plugin you need to declare it in your pom.xml
```
<project>
...
<reporting>
  <plugins>
    <plugin>
      <groupId>fr.ribardiere.maven</groupId>
      <artifactId>howoldaremydependencies-maven-plugin</artifactId>
      <version>0.1-SNAPSHOT</version>
    </plugin>
  </plugins>
</reporting>
...
```

## Detailed description

Algorithm to calculate the global age : 
- we ignore all dependencies not found on Maven Central.
- if no newer dependency can be found on Maven Central, your dependency is considered up to date (age = 0). Else we consider the real age of your dependency. Each dependency age is displayed in the report.
- We then return a summury with : the mean age of found dependencies and the max age.

As soon as a new version of a dependency appears on Maven Central, your project will get suddenly older.

Of course you don't have to necessarily update all your dependencies all the time... but you should verify that you're not getting too old (more than 1 or 2 years old). This will prevent your project from being exposed to security issues or not to be able to find any qualified people on your old stuff.

## Parameters

First version don't need any parameter and only uses maven central repository.
