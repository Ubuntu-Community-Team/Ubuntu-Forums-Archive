---
title: "Installed Oracle JRE 8, but don't see it installed &amp; can't select it"
date: 2021-09-21
forum: General Help
---

### Post by Rick St. George on 2021-09-21
Running UbuntuStudio v20.04

Trying to get Oracle Java selected instead of OpenJDK in order for my Trading Platform to work - using a JNLP file.
It must use the Oracle version. Have installed latest from Oracle from here [https://java.com/en/download/help/linux_x64_install.html]("https://java.com/en/download/help/linux_x64_install.html") 

it installed to dir /usr/lib/jvm/jre1.8.0_301 
but this is what it shows using this command;

```

MS-7640:~$ update-java-alternatives -l
java-1.11.0-openjdk-amd64      1111       /usr/lib/jvm/java-1.11.0-openjdk-amd64
java-1.8.0-openjdk-amd64       1081       /usr/lib/jvm/java-1.8.0-openjdk-amd64

MS-7640:~$ java -version
openjdk version "1.8.0_292"
OpenJDK Runtime Environment (build 1.8.0_292-8u292-b10-0ubuntu1~20.04-b10)
OpenJDK 64-Bit Server VM (build 25.292-b10, mixed mode)

```

I don't see the Oracle version! How can I verify its installed and select it?
Then perhaps my Trading Platform will run (see previous problem posted here via older version of Ubuntu for reference)
[https://ubuntuforums.org/showthread.php?t=2273465&highlight=Java]("https://ubuntuforums.org/showthread.php?t=2273465&highlight=Java")

Iced Tea may be intercepting, and ONLY uses OpenJDK. Don't know if I should Remove it ... or what?
Any help is very appreciated.
Thanks!

---

### Post by monkeybrain20122 on 2021-09-21
Did you setup the alternatives first before you run update alternatives?

The command is 

sudo update-alternatives **--install** ...

see [https://dev.to/thegroo/install-and-manage-multiple-java-versions-on-linux-using-alternatives-5e93](https://dev.to/thegroo/install-and-manage-multiple-java-versions-on-linux-using-alternatives-5e93)

I think java8 is long deprecated.

---

### Post by Rick St. George on 2021-09-21
No I did not ..., but following the instructions, I get the following Error;

```

MS-7640:~$ sudo update-alternatives --install /usr/bin/java OracleJava /usr/lib/jvm/jre1.8.0_301/bin/java 1
update-alternatives: error: alternative link /usr/bin/java is already managed by java

```

I believe the webpage you directed me to, maybe is outdated (Aug 2019), so is it still valid, considering the Error!?!?!

---

### Post by Rick St. George on 2021-09-22
Since the Error reads "managed by Java", then there must be a Java Console. 
But I can't find one, and a search (on the Net) shows nothing. The syntax above follows all installation tutorials I can  find.
So, still at a loss! Any suggestions???

---

### Post by Rick St. George on 2021-09-22
GETTING UBUNTU v20.04 to Recognize / Utilize Oracle JAVA v8

After download and install to this directory "/usr/lib/jvm/jre1.8.0_301/", as mentioned above,I believe this works ... hope it helps someone else!

```

~$ sudo  scite /etc/environment

## MODIFY FILE / ADD FOLLOWING VARIABLES
JAVA_HOME="/usr/lib/jvm/jre1.8.0_301"

## CLOSE SCITE & VERIFY
~$ echo $JAVA_HOME

## UPDATE PROFILE

~$ sudo scite /etc/profile

## MODIFY FILE / ADD THE FOLLOWING
JAVA_HOME=usr/lib/jvm/jre1.8.0_301
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH 

## SAVE FILE & CLOSE SCITE (NANO, etc.)

~$ sudo apt update


~$ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jre1.8.0_301/bin/java" "1000"

~$ java -version
openjdk version "11.0.11" 2021-04-20
OpenJDK Runtime Environment (build 11.0.11+9-Ubuntu-0ubuntu2.20.04)
OpenJDK 64-Bit Server VM (build 11.0.11+9-Ubuntu-0ubuntu2.20.04, mixed mode, sharing)

~$ sudo update-alternatives --config java
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1111      auto mode
* 1            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1111      manual mode
  2            /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java   1081      manual mode
  3            /usr/lib/jvm/jre1.8.0_301/bin/java               1000      manual mode

Press <enter> to keep the current choice[*], or type selection number: 3
update-alternatives: using /usr/lib/jvm/jre1.8.0_301/bin/java to provide /usr/bin/java (java) in manual mode

~$ java -version
java version "1.8.0_301"
Java(TM) SE Runtime Environment (build 1.8.0_301-b09)
Java HotSpot(TM) 64-Bit Server VM (build 25.301-b09, mixed mode)

~$ sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jre1.8.0_301/bin/javaws" "1000"

~$ sudo update-alternatives --config javaws
There are 2 choices for the alternative javaws (providing /usr/bin/javaws).

  Selection    Path                                  Priority   Status
------------------------------------------------------------
* 0            /usr/lib/icedtea-web/bin/javaws        1101      auto mode
  1            /usr/lib/icedtea-web/bin/javaws        1101      manual mode
  2            /usr/lib/jvm/jre1.8.0_301/bin/javaws   1000      manual mode

Press <enter> to keep the current choice[*], or type selection number: 2
update-alternatives: using /usr/lib/jvm/jre1.8.0_301/bin/javaws to provide /usr/bin/javaws (javaws) in manual mode

```

---

