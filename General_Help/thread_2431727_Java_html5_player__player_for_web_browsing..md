---
title: "Java html5 player  player for web browsing."
date: 2019-11-20
forum: General Help
---

### Post by dan369 on 2019-11-20
Hi i'm new to ubuntu. I tried watching a video on a website however it said the video could not be played. I tried to download java but its a little overwhelming. I just need it for my web browser firefox. I went through a lot of tutorials and don't know what one 1 need, and most were unhelpful. These are the ones i have been trying to use.  Help would be appreciated!!


[http://ubuntuhandbook.org/index.php/2018/11/how-to-install-oracle-java-11-in-ubuntu-18-04-18-10/](http://ubuntuhandbook.org/index.php/2018/11/how-to-install-oracle-java-11-in-ubuntu-18-04-18-10/)
[https://www.wikihow.com/Install-Java-on-Ubuntu](https://www.wikihow.com/Install-Java-on-Ubuntu)
[https://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux](https://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux)
[https://www.wikihow.com/Install-Java-on-Ubuntu](https://www.wikihow.com/Install-Java-on-Ubuntu)
[https://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux](https://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux) On this one i got Package 'jre' has no installation candidate

---

### Post by deadflowr on 2019-11-20
What Ubuntu version are you on?

---

### Post by dan369 on 2019-11-22
The most recent ubuntu desk top 18.04 LTS. I downloaded and installed on a old computer yesterday. Most of the tutorials gives me this message in the process  Package 'jre' has no installation candidate. I would also like to know if I posted this in the wrong place. I probably did. lol but its here so any help would be nice.

---

### Post by deadflowr on 2019-11-22
*Thread moved to **General Help***

---

### Post by dan369 on 2019-11-22
Thankyou!! Some of the JW players are not working. I don't know how to  get java for jw players on my web browser. I assume its because i don't  have java downloaded. I don't know what tutorial I need. 

I guess it might be this one [http://ubuntuhandbook.org/index.php/...u-18-04-18-10/]("http://ubuntuhandbook.org/index.php/2018/11/how-to-install-oracle-java-11-in-ubuntu-18-04-18-10/")  but i can't be sure.  This might sound silly but i don't know what this  means. UPDATE: Oracle Java 11 can&#8217;t be directly downloaded from Oracle  website any more! Now you **HAVE** to log in and manually download Oracle Java 11 .tar.gz, and place the archive in /var/cache/oracle-jdk11-installer-local/ This part confuses me the most. "Now you **HAVE** to log in" Log into where?

---

### Post by albel2 on 2019-12-25
> **dan369 said:**
> Now you **HAVE** to log in and manually download Oracle Java 11 .tar.gz, and place the archive in /var/cache/oracle-jdk11-installer-local/ This part confuses me the most.
[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

### Post by Holger_Gehrke on 2019-12-26
I don't think you need Java for that. Current versions of jwplayer use Java**Script** which is something completely different from Java and is built into the browser. Which is a good thing since all major browser have deprecated the **A**pplication **P**rogramming **I**nterface needed for using Java in a browser. Older versions of jwplayer were written using Flash, so if you're trying to watch videos on sites which still use old players than that's what you need. The easiest way to get flash and make it keep current automatically is to install the package flashplugin-installer ('sudo apt install flashplugin-installer' in a terminal). Even that is bound to go away someday soon since Adobe has announced that Flash will go EOL at the end of 2020, at which point browser makers will probably remove the last remains of the Netscape Plugin **API**.

Holger

---

