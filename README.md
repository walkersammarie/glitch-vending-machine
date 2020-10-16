## Overview
To run a Java command-line program as a project on [Glitch](https://glitch.com):
1. Fork this repository.
1. Replace `my_app.jar` with your own jar (named `my_app.jar`, or update `start.sh` with your jar name).
1. On Glitch, select New Project > Clone from Git Repo, and select your fork of this repository.

## How to create my_app.jar (using Maven and the Spring Boot Maven plugin)

* Add this section to your pom.xml file within project/build/plugins, replacing `com.example.main` with the class that contains the main method you want to execute:
```
<plugin>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-maven-plugin</artifactId>
  <configuration>
    <mainClass>
      com.example.main
    </mainClass>
  </configuration>
</plugin>
```
* If that plugin isn't found, also add this section to your pom.xml:
```
<repositories>
  <repository>
      <id>spring-repo</id>
      <url>https://repo.spring.io/release</url>
    </repository>
</repositories>
```
* Build the jar by running `mvn clean package spring-boot:repackage`
* Find the resulting jar in the target directory, rename it to `my_app.jar` and confirm it runs with `java -jar my_app.jar`
