---
title: "Running java program"
date: 2013-08-23
forum: General Help
---

### Post by Margaret Dumont on 2013-08-23
Hello everybody,

I am running Ubuntu 12.04 LTS (Precise Pangolin) and I am trying to install Thinking Rock 2.2.1, which is in principle programed in Java 1.6.

I've run "java -version" to make sure I already have it and I get:

```
java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.6) (6b27-1.12.6-1ubuntu0.12.04.2)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)
```


The Thinking Rock developers provide its source code and two versions, one with java and the other without:
[http://sourceforge.net/projects/thinkingrock/files/ThinkingRock/TR%202.2.1/](http://sourceforge.net/projects/thinkingrock/files/ThinkingRock/TR%202.2.1/)

I've downloaded both versions and tried the installation instructions they provide: 
[LIST=1]
[*]make sure that you have java 1.6 installed,
[*]make sure you have xdg-email and xdg-opne in the /usr/bin/ folder,
[*]run "tr.sh".
[/LIST]

I feel very silly but I don't seem to be able to run it.

I've tried by typing "tr.sh" in the terminal within the folder where I extracted the files, but I get the answer "Command not found" and I've also tried to type "tr" but then an unrelated translation program opens. 

Finally I've also tried "java tr.sh" and "java tr" but it complains about not finding the main class.


Then I found out that Crazyscot had compiled packages for previous Ubuntu versions:
[https://launchpad.net/~crazyscot/+archive/tr/+packages](https://launchpad.net/~crazyscot/+archive/tr/+packages)

So I've also tried downloading the .deb package of the latest available version (Natty), which is opened by "Ubuntu software center" on double click and seems to install with no problem. However, when I click on the launcher icon, the thing flashes a couple of times and then nothing happens.

Then I tried to run "thinkingrock" on the terminal to see if I could get some kind of error message and I got  "Cannot find java. Please use the --jdkhome switch.".


Does any of you know how could I run the java program, and/or how can I use the "--jdkhome switch" while running "thinkingrock"?

Many thanks in advance,

M

---

### Post by Margaret Dumont on 2013-08-23
I've reread [this thread]("http://ubuntuforums.org/showthread.php?t=1591604&p=10139330#post10139330") and it occurred to me to write in the terminal not only the program name "tr.sh" but also the whole path. And this has finally opened the program.

I am wondering now why is it necessary to write the whole path to run the file, taking into account that I am already in the right folder. 

Is it because there is this other translation program installed called "tr"? How can I change one by the other in my system so that Thinking Rock will be the default program?

Many thanks,

M

---

### Post by davetv on 2013-08-23
If you are in a terminal and want to run a script in the current folder, you have to enter

./tr.sh

---

### Post by Margaret Dumont on 2013-08-24
Dear davetv,

Thank you for your answer. I saw afterwards that I had a much simpler problem than I thought... In fact I had essentially a newbie question.  :)

Installing now the program succesfully to a second computer.

Best regards!

M

PD: Maybe a moderator should change the title and move it to another section of the forum?

---

### Post by Margaret Dumont on 2013-08-26
Dear all,

I'm afraid I was too quick to mark this problem as "Solved". 

Today when I opened the program in my desktop at work, it was complaining all the time about not finding the class "tr.model.topic.Topic" and I couldn't load any of the projects that I created on Friday.  :(

It gives me always the same error as I try to open any saved file:

```

The data file could not be read due to the following error:

Cannot find class tr.model.topic.Topic
----Debugging information ----
message        : Cannot find class tr.model.topic.Topic
line number    : 1
path        : /data/topics/items/topic
cause-message    : Cannot find class tr.model.topic.Topic
class        : tr.model.Data
cause-exception    : com.thoughtworks.xstream.converters.reflection.ObjectAccessException
required-type    : tr.model.topic.Topic
------------------------

Do you want to try to restore from the last recovery file?
```

Clicking "Ok" yields: 
```

Open file error

The data file could not be opened.
The data file could not be recovered.
```

The strange thing is that I believe it is working fine in my laptop. 

Does any of the java initiated people have any idea of what could I try to fix it?

Many thanks,

M.

---

### Post by Margaret Dumont on 2013-08-26
Hello,

I've tried to open in my laptop the projects that I saved in my desktop and there isn't any problem, so the saving procedure of the program is working correctly. 

So it is probably true that the conflict is arising from a java class that the program calls on opening.

Any ideas on how to find the problem and fix it?

Thanks!

M.

---

### Post by Margaret Dumont on 2013-08-27
Hi everyone,

I've finally solved it!   :)

I found the solution hidden in this thread in German:
[http://www.thinkingrock.de/forum/5-installation/77-umstellung-auf-deutsch-klappt-nur-1-2.html](http://www.thinkingrock.de/forum/5-installation/77-umstellung-auf-deutsch-klappt-nur-1-2.html)

It seems that early versions of ThinkingRock (such as one that has been open sourced) do not work with newer versions of java.

So, what I did: 

1.- I ran this command on the terminal (thanks Crazyscot!):  :)
```
update-java-alternatives --jre -l
``` and I got this:```
java-1.6.0-openjdk-amd64 1061 /usr/lib/jvm/java-1.6.0-openjdk-amd64
java-1.7.0-openjdk-amd64 1051 /usr/lib/jvm/java-1.7.0-openjdk-amd64
```


2.- With this information I opened the configuration file of Thinking Rock, which can be found in the "*etc*" folder of the program path, with gedit. In my case, ```
gedit ~/Programari/tr-2.2.1/etc/tr.conf
```

3.- I located the line that specifies the Java JDK/JRE path which should be used by the program, and then wrote the path for version 1.6 that I had obtained in step 1 and uncommented the line. So, in my case, I had to change the line ```
#jdkhome="/path/to/jdk"
``` by the line ```
jdkhome="/usr/lib/jvm/java-1.6.0-openjdk-amd64"
```

So now it works perfectly.  :)

I hope it is useful to someone else.

Best regards,

M.

---

