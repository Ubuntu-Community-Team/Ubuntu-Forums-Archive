---
title: "help install. new frostwire"
date: 2006-11-26
forum: General Help
---

### Post by DougieFresh4U on 2006-11-26
sassy@SassysFunBox:~$ sudo mkdir /usr/java
mkdir: cannot create directory `/usr/java': File exists
sassy@SassysFunBox:~$ sudo cp jre-1_5_0_09-linux-i586.bin /usr/java
cp: cannot stat `jre-1_5_0_09-linux-i586.bin': No such file or directory
     I am helping some one install new frostwire from how-to but I am having a bit of trouble with where this java is, it is in usr but next step it says not there . I have posted what happened from terminal. I'm confused

---

### Post by meng on 2006-11-26
> **DougieFresh4U said:**
> sassy@SassysFunBox:~$ sudo mkdir /usr/java
mkdir: cannot create directory `/usr/java': File exists
The file/directory already exists, not much of a mystery here.
> sassy@SassysFunBox:~$ sudo cp jre-1_5_0_09-linux-i586.bin /usr/java
cp: cannot stat `jre-1_5_0_09-linux-i586.bin': No such file or directory
This means there is no file jre-1_5_[etc] in the home directory. Perhaps you meant to navigate to another directory? Perhaps try:
locate jre-1

---

### Post by DougieFresh4U on 2006-11-26
Arrow  	
HOW-TO Install Frostwire 4.13.1    I am following the mentioned link. java is in usr some from what I posted ealier what am I doing wrong please & good morning meng :)actually, I shall wait until there is an EASY deb file made for it and for now the old Frostwire will suffice -**[B]-Mods, consider this tread Closed/Dead**[/B]

---

### Post by taurus on 2006-11-26
Frostwire (and java) is available from automatix2!!!

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by motorhead on 2006-11-27
> **DougieFresh4U said:**
> Arrow  	
HOW-TO Install Frostwire 4.13.1    I am following the mentioned link. java is in usr some from what I posted ealier what am I doing wrong please & good morning meng :)actually, I shall wait until there is an EASY deb file made for it and for now the old Frostwire will suffice -**[B]-Mods, consider this tread Closed/Dead**[/B]

you're getting that error because you need to put the java package in the home directory or just give the right direction. I guess you downloaded jre on desktop, so the code must be like this:

sudo cp ./Desktop/jre-1_5_0_09-linux-i586.bin /usr/java

---

### Post by DougieFresh4U on 2006-11-28
Thank you motorhead, that worked out for(the code change you made for me)

---

### Post by motorhead on 2006-11-28
welcome ^^

---

