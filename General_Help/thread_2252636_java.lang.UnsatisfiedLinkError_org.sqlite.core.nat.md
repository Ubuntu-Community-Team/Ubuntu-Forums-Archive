---
title: "java.lang.UnsatisfiedLinkError: org.sqlite.core.nativeDB.open()"
date: 2014-11-13
forum: General Help
---

### Post by Don_Joe on 2014-11-13
[FONT=Arial]First off, I dabble with Java and I dabble with Linux by no means am I a pro! [/FONT]

[FONT=Arial]I have built a Java app that uses SQLite (sqlite-jdbc-3.8.7.jar) and have rolled everything into a jar file. Running the jar file on windows works as expected however, trying to run it on Ubuntu Server 14.04 has turned into quite a task! I put together a brand new virtual machine in VirtualBox for testing. I installed Java (sudo apt-get install default-jre) and have tried installing SQLite both from the repositories and by downloading the tar and compiling. SQLite installs just fine both ways as I can access it from terminal. I created a new sub-directory within my home directory and copied over my app jar file. From terminal, I then run the command: sudo java -jar <jar-name>.jar and I receive a java.lang.[/FONT][FONT=Arial]unsatisfiedlinkerror. See the attached image, what else must be done to get this working on Ubuntu? Any help would be appreciated!


[/FONT]

---

