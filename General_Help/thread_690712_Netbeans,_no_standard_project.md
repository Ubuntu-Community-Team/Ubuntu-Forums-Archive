---
title: "Netbeans, no standard project"
date: 2008-02-07
forum: General Help
---

### Post by aerofoil on 2008-02-07
Hi all

I have been trying to install netbeans, but have come across a problem. 

It seemed to install OK, then when i ran the program, it gave a warning message saying something about the JDK and having to install something else. I stupidly ignored this and clicked disable and continue. 

When I tried to make a new program, file>new, the only options available was for a java project with existing ant script. I really need to have the option for just a standard new java project, but this option is not available to me!

I know I have been stupid, really should have noted what the message said. I have reinstalled a few times, marked for complete removal etc, but it will not show me that message again, or show me the option to create a new standard project. 

I have the java 6 jdk installed. Does anyone have any ideas?

Thanks

---

### Post by mer on 2008-04-01
If you are still interested or for anyone googling: [http://tamastarjanyi.blogspot.com/2008/01/netbeans-missing-new-project-categories.html]("http://tamastarjanyi.blogspot.com/2008/01/netbeans-missing-new-project-categories.html")

From what I gather, netbeans is looking in the wrong place for the project templates. Two commands are needed:

rm -rf ~/.netbeans/6.0/config/Modules
netbeans --jdkome /usr/lib/jvm/java-6-sun

The first deletes the setting to look in the wrong place and the second starts netbeans and sets it to use the correct settings. You only need to start this way once. This worked for me with Java 6 JDK installed. Hope this helps someone.

---

