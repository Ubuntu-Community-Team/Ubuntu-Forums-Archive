---
title: "Executing jar file from GUI File Manager"
date: 2015-01-04
forum: General Help
---

### Post by iamcreasy2 on 2015-01-04
I know that I can execute a **.jar** file using the command **java -jar file_name.jar **on terminal.

How can I execute the jar file from GUI File Manager, by double clicking on it?

Note:
I have installed Oracle Java following [this]("http://askubuntu.com/questions/56104/how-can-i-install-sun-oracles-proprietary-java-jdk-6-7-8-or-jre") method. Java is not shown on the list : file_name(context menu) > Open With > Other Application... > Show Other Applications
When I run** java -version** on terminal it returns positive, and I am using Ubuntu 14.04.

---

### Post by slickymaster on 2015-01-05
Hi iamcreasy2, welcome to the forums.

> **iamcreasy2 said:**
> I know that I can execute a **.jar** file using the command **java -jar file_name.jar **on terminal.

How can I execute the jar file from GUI File Manager, by double clicking on it?
To open jar files by double clicking them, do the following:

[LIST]
[*]Right click the jar file > Properties.
[*]Click on the &#8220;Open With&#8221; option.
[*]Change the default choice to whatever Java runtime environment (JRE) you have installed.
[*]Click close and you should be ready to double click.
[/LIST]

> **iamcreasy2 said:**
> Note:
I have installed Oracle Java following [this]("http://askubuntu.com/questions/56104/how-can-i-install-sun-oracles-proprietary-java-jdk-6-7-8-or-jre") method. Java is not shown on the list : file_name(context menu) > Open With > Other Application... > Show Other Applications
When I run** java -version** on terminal it returns positive, and I am using Ubuntu 14.04.
A clean and easier way to install Java is via a PPA repository, allowing you to get its updates through the update manager not only for JDK, but also for JRE and the Java browser plugin.

All that needs to be done is to run the following at a terminal window:```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

---

