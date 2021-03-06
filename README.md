# Autocompile-scss-in-springboot

The project structure:

![alt text](https://github.com/taylorhelene/Autocompile-scss-in-springboot/blob/main/Images/one.png)

Adding scss Document:

![alt text](https://github.com/taylorhelene/Autocompile-scss-in-springboot/blob/main/Images/two.png)

Pom file:


    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <parent>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-parent</artifactId>
            <version>2.6.3</version>
            <relativePath/> <!-- lookup parent from repository -->
        </parent>
        <groupId>convert</groupId>
        <artifactId>convert</artifactId>
        <version>0.0.1-SNAPSHOT</version>
        <name>convert</name>
        <description>Demo project for Spring Boot</description>
        <properties>
            <java.version>17</java.version>
        </properties>
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-thymeleaf</artifactId>
            </dependency>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-web</artifactId>
            </dependency>

            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-devtools</artifactId>
                <scope>runtime</scope>
                <optional>true</optional>
            </dependency>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-test</artifactId>
                <scope>test</scope>
            </dependency>
        </dependencies>

        <build>
            <plugins>
                <plugin>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-maven-plugin</artifactId>
                </plugin>
                <!-- Sass compiler -->
                <plugin>
                    <groupId>org.jasig.maven</groupId>
                    <artifactId>sass-maven-plugin</artifactId>
                    <version>1.1.1</version>
                    <executions>
                        <execution>
                            <phase>prepare-package</phase>
                            <goals>
                                <goal>update-stylesheets</goal>
                            </goals>
                        </execution>
                    </executions>
                    <configuration>
                        <resources>
                            <resource>
                                <!-- Set source and destination dirs -->
                                <source>
                                    <directory>${project.basedir}/src/main/resources/static/saas/</directory>
                                </source>
                                <destination>${project.basedir}/src/main/resources/static/css</destination>
                            </resource>
                        </resources>
                    </configuration>
                </plugin>
            </plugins>
        </build>
    </project>

Run sass watcher:

For hot-deploy auto compiling run sass-maven-plugin’s watch goal:

    mvn sass:watch



Do some changes in styles.scss, save it and check browser again without restarting web server.

