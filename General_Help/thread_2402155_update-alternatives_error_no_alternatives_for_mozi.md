---
title: "update-alternatives: error: no alternatives for mozilla-javaplugin.so"
date: 2018-09-26
forum: General Help
---

### Post by diederick2 on 2018-09-26
I'm trying to switch to jdk11 In Bionic. Installation went fine:

```
$ sudo update-java-alternatives -l
java-1.11.0-openjdk-amd64      1101       /usr/lib/jvm/java-1.11.0-openjdk-amd64
java-1.8.0-openjdk-amd64       1081       /usr/lib/jvm/java-1.8.0-openjdk-amd64
```

So I thought I could switch by:

```
$ sudo update-java-alternatives -s java-1.11.0-openjdk-amd64
```

However, that returns:

```
update-alternatives: error: no alternatives for mozilla-javaplugin.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-11-openjdk-amd64/lib/IcedTeaPlugin.so

```

That file does indeed not exist, but neither does it in /usr/lib/jvm/java-1.8.0-openjdk-amd64. The same goes for mozilla-javaplugin.so. So why does update-alternatives complain about it not being available, and how can I make it stop caring?

Thanks for any help!

---

### Post by diederick2 on 2018-09-27
Okay, so when I do 

```

$ sudo update-alternatives --config java

```

Then I get this:

```

There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1101      auto mode
* 1            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1101      manual mode
  2            /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java   1081      manual mode

```

Now I can make a selection without the aformentioned error, but  it raises more questions:
[LIST=1]
[*] Why does it say 2 choices, when it offers 3? 
[*]Why am I still "in" jdk 10, when I select either of the jdk11 options? 
[/LIST]
 
```

$ java -version
openjdk version "10.0.2" 2018-07-17
OpenJDK Runtime Environment (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.2)
OpenJDK 64-Bit Server VM (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.2, mixed mode)

```

Can anyone tell me how to configure my system to use jdk11?

---

