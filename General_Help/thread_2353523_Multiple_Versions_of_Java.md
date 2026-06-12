---
title: "Multiple Versions of Java?"
date: 2017-02-22
forum: General Help
---

### Post by chondromalasia on 2017-02-22
Hi. I need to run a piece of software and it needs to run 1.6 (or maybe 1.7) of java runtime (I'm currently up to date with 1.8). How do I install the earlier version and still keep 1.8? In the program in question I can change its 'Java home' Path. Is it just as simple as downloading the older version and installing it? I also want to make sure that everything still 'points' to the most current version of java. I found these links:

[https://ubuntuforums.org/showthread.php?t=1398360](https://ubuntuforums.org/showthread.php?t=1398360)
[https://ubuntuforums.org/showthread.php?t=1562886](https://ubuntuforums.org/showthread.php?t=1562886)

Does this stuff get me where I want? Thanks in advance.

---

### Post by dragonfly41 on 2017-02-22
You will need to install update-java-alternatives to switch between java versions using command line

[http://askubuntu.com/questions/599105/using-alternatives-with-java-7-and-java-8-on-14-04-2-lts](http://askubuntu.com/questions/599105/using-alternatives-with-java-7-and-java-8-on-14-04-2-lts)

---

### Post by ajgreeny on 2017-02-22
Java 1.6 is full of security holes so I would avoid using anything that needs that version if possible, and if you must use it, keep ofline.

---

### Post by chondromalasia on 2017-02-23
> **ajgreeny said:**
> Java 1.6 is full of security holes so I would avoid using anything that needs that version if possible, and if you must use it, keep ofline.

Yeah this is my exact issue. And in looking at the above answer, it looks like this is possible. Do you have any advice for 'keeping it offline'?

---

### Post by ajgreeny on 2017-02-23
Switch off networking while you are using java 1.6 from the network icon in your panel.

---

### Post by chondromalasia on 2017-02-23
> **ajgreeny said:**
> Switch off networking while you are using java 1.6 from the network icon in your panel.

That won't really work for me. However, it gave me an idea, and I think I'm just going to make a virtual machine for it, if you think that will work.

---

### Post by Olav on 2017-02-23
There is no need to be so paranoid. You could just download JRE 1.6 and unpack it somewhere, and make a simple script to start your program using that environment. I believe there are a few environment variables you may need to set in your script, you could look that up.

In any case do **not** use update-java-alternatives and 1.8 will remain the system wide default for all other applications. As long as nothing else uses your separate JRE 1.6, and your application does not do anything weird, it will be quite safe.

---

### Post by chondromalasia on 2017-02-23
> **Olav said:**
> There is no need to be so paranoid. You could just download JRE 1.6 and unpack it somewhere, and make a simple script to start your program using that environment. I believe there are a few environment variables you may need to set in your script, you could look that up.

In any case do **not** use update-java-alternatives and 1.8 will remain the system wide default for all other applications. As long as nothing else uses your separate JRE 1.6, and your application does not do anything weird, it will be quite safe.

Awesome thanks. Yeah that looked sketchy. I was just wondering if there was something that was part of the installation process that would make applications point to it. I know for certain I can change the environmental variables to point to a different version of Java.

---

### Post by Olav on 2017-02-23
> **chondromalasia said:**
> I was just wondering if there was something that was part of the installation process that would make applications point to it.

If you download the Linux .bin file from [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase6-419409.html#jre-6u45-oth-JPR) there is no installation process as such. It is a "self extracting archive" that will just unpack the JRE files into a directory. You can move that anywhere you like, somewhere under /opt would be a good choice. You could probably even move it to the directory where your application resides.

---

### Post by chondromalasia on 2017-02-24
> **Olav said:**
>  You can move that anywhere you like, somewhere under /opt would be a good choice. You could probably even move it to the directory where your application resides.

Dingdingding. This is the perfect answer. Thanks.

---

