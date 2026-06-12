---
title: "Java problems"
date: 2015-04-23
forum: General Help
---

### Post by zach31 on 2015-04-23
I started up my computer like normal, and found that Java was no longer working with any of my Java-reliant applications, I tried reinstalling Java but it still didn't work, this was on Xubuntu 14.04.2, I'm very new to Linux and don't know how I'd go about fixing this any help would be greatly appreciated, thanks in advance. :)

---

### Post by Geoffrey_Arndt on 2015-04-23
So, what does the Ubuntu Software Center show when querying on "java" . . . the buntu distros use open -java jdk runtime (version 7).  Try resinstalling from repo.

---

### Post by Bucky Ball on 2015-04-23
Xubuntu uses Synaptic Package Manager rather than SCentre. ;)

Yes, check you have openjdk-7-jre installed and icedtea-7 also using Synaptics. Odd how java disappeared like that, though. :-k

---

### Post by zach31 on 2015-04-24
Thanks for trying to help but this did not solve my issue, or it might of been siomething I did wrong, so could you give me more of a step by step help

---

### Post by Morbius1 on 2015-04-24
Please post the output of the following command:
```
ls -al /usr/share/applications | grep java
```
[COLOR=#0000cd]**EDIT**[/COLOR]: I was supposed to ask a question first: Are you talking about executing jar files?

---

### Post by zach31 on 2015-04-24
Yes, I was, and here's the output of that command.
grep java
-rw-r--r--   1 root root   300 Apr 14  2014 icedtea-netx-javaws.desktop


It's sort of odd that only the icedtea thing is showing up, as the Ubuntu Software Center shows that I have Java 7 installed...

---

### Post by Bucky Ball on 2015-04-25
> **zach31 said:**
> Yes, I was, and here's the output of that command.
grep java
-rw-r--r--   1 root root   300 Apr 14  2014 icedtea-netx-javaws.desktop


Did you issue the entire command?

```
ls -al /usr/share/applications | grep java
```

I get exactly the same so nothing amiss there I wouldn't think:

```
-rw-r--r--   1 root root   300 Apr 15  2014 icedtea-netx-javaws.desktop
```


PS: Please use [code] tags for terminal output. Keeps the formatting, neater and easier to distinguish among the other text. See the last link in my signature for how. ;)

---

### Post by Morbius1 on 2015-04-25
The problem is something is missing. When java was updated the package engineer forgot to add a file: **openjdk-7-java.desktop**

It was there before the update but removed after the update.

My suggestion is to create your own file association for a jar file:

Right click any jar file.
Select "Open with other application"
At the bottom of the dialogue box select "Use a custom command"
And enter the following:
```
java -jar
```
It should look like this:[ATTACH=CONFIG]261519[/ATTACH]

You'll be immune from this happening again and as a side benefit you will no longer get that silly error message telling you that a jar file needs to be made executable to run.

---

