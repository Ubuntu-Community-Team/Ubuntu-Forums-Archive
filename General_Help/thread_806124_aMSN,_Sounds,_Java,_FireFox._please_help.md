---
title: "aMSN, Sounds, Java, FireFox. please help"
date: 2008-05-24
forum: General Help
---

### Post by Linux_noob616 on 2008-05-24
Hi, i have a questions and as the name implies i am a total Linux noob, Ubuntu is my first installation of Linux and so far i am liking it but stuck on a few things...:confused:

For starters i am using Ubuntu 8.04 LTS 64 Bit. 

mainly (i think they might stem from the same problem) but my aMSN has no flashes or sounds when i get a message or send one. Secondly the only sounds i hear (outside of music) is the one start up, and log on sounds.

Secondly, I can't get Java to work. I installed it though the package manager, and i also installed the restricted extras pack as well as the GCJ plugin for firefox. Still nothing.

Also How do i update from Beta 5 to RC1 in FireFox?

And lastly. this is my PC and it's drivers. i know i have the video drivers but i don't know all the parts outside RAM and processor.

so if this is any help.

[http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=Windows%20Vista%20(32-bit](http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=Windows%20Vista%20(32-bit))

thanks to anyone who can help me.

---

### Post by UK-Wobbie on 2008-05-24
> **Linux_noob616 said:**
> Hi, i have a questions and as the name implies i am a total Linux noob, Ubuntu is my first installation of Linux and so far i am liking it but stuck on a few things...:confused:

For starters i am using Ubuntu 8.04 LTS 64 Bit. 

mainly (i think they might stem from the same problem) but my aMSN has no flashes or sounds when i get a message or send one. Secondly the only sounds i hear (outside of music) is the one start up, and log on sounds.

Secondly, I can't get Java to work. I installed it though the package manager, and i also installed the restricted extras pack as well as the GCJ plugin for firefox. Still nothing.

Also How do i update from Beta 5 to RC1 in FireFox?

And lastly. this is my PC and it's drivers. i know i have the video drivers but i don't know all the parts outside RAM and processor.

so if this is any help.

[http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=Windows%20Vista%20(32-bit](http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=Windows%20Vista%20(32-bit))

thanks to anyone who can help me.


On aMsn you may need to put "aplay $sound" in "Sound Server" in "Others" in "Preferences" to get sound..

Firefox Java, You may need to install all the right Java plugins or go on a Java chat room to get the Java plugin to pop up!

Give this a go 
[sun-java6-bin]("apt://sun-java6-bin")
[sun-java6-jre]("apt://sun-java6-jre")
[sun-java6-plugin]("apt://sun-java6-plugin")


Beta 5 of firefox is the new one out right now.

The pc info? What do you need to know :)

---

### Post by Linux_noob616 on 2008-05-24
Tried what you said about Java, and i had everything else but this is what i got about the plugin.
> "sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate"

> On aMsn you may need to put "aplay $sound" in "Sound Server" in "Others" in "Preferences" to get sound..

Thanks it worked =]

---

### Post by Linux_noob616 on 2008-05-24
So no-one knows anything about the FireFox RC1??

(this is just a bump):guitar:

---

### Post by mano cazalet on 2008-05-24
I wouldn't update yet. It will be in the repos and official updates in a day or two. Just let the guys come back from Prague :)

[http://ubuntuforums.org/showpost.php?p=5012863&postcount=8](http://ubuntuforums.org/showpost.php?p=5012863&postcount=8)

as for bumping I guess there is an unwritten agreement here, that it should not be before 24 hours (more or less) ;)

---

### Post by Linux_noob616 on 2008-05-24
Okay thanks.

Still no Java plugin thing though eh?

---

### Post by mano cazalet on 2008-05-24
oops i missed that you are on 64bits
(any specific reason for that?)

2 hopefully useful links:

[https://bugs.launchpad.net/sun-java/+bug/104512](https://bugs.launchpad.net/sun-java/+bug/104512)

[http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)

---

### Post by Linux_noob616 on 2008-05-24
Cause i have a 64bit processor, wouldn't it be best to have a 64 bit OS?

So does everyone except Mac hate us 64 bit users? =/ Cause i'm always seeing bugs bugs bugs.

---

### Post by mano cazalet on 2008-05-25
i guess its ok, but im running 32bits on a 64 machine coz sometimes things need a little more fixing for 64bit OS

---

### Post by Linux_noob616 on 2008-05-25
Oh i see. Well i don't use Java to much, but it was working thats whats odd =/ Anyway thanks for your help.

---

