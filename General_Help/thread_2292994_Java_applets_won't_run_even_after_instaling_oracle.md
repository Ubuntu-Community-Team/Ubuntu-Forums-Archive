---
title: "Java applets won't run even after instaling oracle jdk."
date: 2015-09-01
forum: General Help
---

### Post by Avinash_Pandey on 2015-09-01
I am new to ubuntu. I am using it since last month. I tried to install oracle-jdk (which includes jre) so that I can run java applets. I *strictly* followed the "Manual Install" process written on the following page by Salem.
[http://askubuntu.com/questions/521145/how-to-install-oracle-java-on-ubuntu-14-04](http://askubuntu.com/questions/521145/how-to-install-oracle-java-on-ubuntu-14-04)
I retianed the installation directories as told in above post and also created the required oraclejdk.sh file.

After installing I restarted my laptop and ran in terminal the following
[COLOR=#111111][FONT=Consolas]source /etc/profile.d/oraclejdk.sh[/FONT][/COLOR]
Before installing java, when I typed **java** in the terminal, it gave me suggestion about what packages include java.
After installing java, when I enquire **java** in the terminal, it prints a whole lots of stuff (see the pic; I think it means that java is installed on the system.)

But I am unable to run any java applets online in both Chrome (version is above 42) and Mozilla Firefox. I don't see java in my plugins list in Firefox.
What I did wrong? How to make use of the useless pieces which I installed? Or how to remove the installation and install properly oracle jdk (I prefer oracle jdk over openjdk)?
I use Ubuntu vivid 15.04 64-bit.

[[img]http://s28.postimg.org/rwqnvm0g9/Screenshot_from_2015_09_02_01_07_00.jpg[/img]](http://postimg.org/image/rwqnvm0g9/)

---

### Post by monkeybrain20122 on 2015-09-01
You could have just installed openjdk and the icedtea plugin from the repository. There is no advantage or need for using Oracle's jave unless you use some applications that explicitly requires it. And if you install oracle java you should have gone the ppa route from your link instead of doing it manually. You can just delete manually all the files you have installed.

---

### Post by efflandt on 2015-09-02
Google Chrome browser no longer does NPAPI (Netscape Plugins), therefore, no longer does Java. [http://blog.chromium.org/2014/11/the-final-countdown-for-npapi.html](http://blog.chromium.org/2014/11/the-final-countdown-for-npapi.html)

Installing a jdk or jre allows you to run java jar files from a terminal (java -jar whatever.jar), but you need a browser plugin to do java applets from a web browser (like Firefox). As mentioned, in Ubuntu that is typically an **openjdk** jre package (I am using openjdk-7-jre) for java and **icedtea-plugin** unless you do something that specifically requires Oracle Java. But I have not used Oracle Java, so do not know what browser plugin it needs. The only thing I use java for is minecraft and that has always worked fine with openjdk.

---

