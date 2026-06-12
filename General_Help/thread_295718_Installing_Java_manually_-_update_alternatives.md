---
title: "Installing Java manually - update alternatives?"
date: 2006-11-08
forum: General Help
---

### Post by eagle63 on 2006-11-08
Ok, this has probably been answered before but I did a ton of searching and couldn't find the answer.  I've already installed the Java 5 JDK using Synaptic and it worked great.  Following the wiki, I did the "update-alternatives" thing and set it to point to the new java-1.5.0_06.  I then updated /etc/jvm and re-ordered the list of java installs.  

Now however, I want to install a newer version as there was a major bug fix in update 8 that fixes the slow debug problem on Linux.  Anyway, since the package in Synaptic is still at _06 and I need _08 or higher, I decided to download jdk1.5.0_09 from Sun's website.  I executed the .bin file and it extracted all the files, etc.  

So my question is, how do I get Ubuntu to "recognize" this new version of Java?  If I run "update-java-alternatives -l" it doesn't list it as an available option.  Similarly, if I type java -version, it still shows my previous version that I installed through Synaptic.  Should I just add it to the $PATH variable?  Do I even need to mess with the update-alternatives thing??

Thanks in advance for any help!!

---

### Post by steve.horsley on 2006-11-08
I've done it by changing the symlink in /etc/alternatives. I think that this is what update-alternatives would end up doing.

I found the alternatives link by doing **which java** and then following the symlink chain.

---

### Post by eagle63 on 2006-11-08
Thanks Steve, that makes sense.  For me, /usr/bin/java is linked to /etc/alternatives/java, which is then linked to the "old" jdk.  So if I understand this correctly I need to change the link on /etc/alternatives/java to point to my new jdk.  

I've tried doing:
ln -s /etc/alternatives/java /usr/lib/jvm/newjdkpath but it just gives me the message, "ln: creating symbolic link 'usr/lib/jvm/jdk1.5.0_09' to '/etc/alternatives/java': File exists"

But it doesn't appear that the link got created.  I know this is a newb question, but could you show me how to link these 2 files correctly?? 

Thanks!

---

### Post by steve.horsley on 2006-11-09
You have to delete the old symlink first:
[B]cd /etc/alternatives
sudo rm java
sudo ln -s /whereverTheNewOneIs/java java[/B]

---

### Post by eagle63 on 2006-11-09
thanks, that did it!

---

### Post by zadax on 2006-11-11
[http://www.ubuntuforums.org/showthread.php?t=297770](http://www.ubuntuforums.org/showthread.php?t=297770)

HTH

---

### Post by eagle63 on 2006-11-12
Thnanks Zadax, looks like you were trying to get around the same slow debugging issue I was with jdk 1.5.0_06. :) 

The method you chose looks quite a bit more involved than what I did, but it's probably more thorough too.  Since mine seems to be working fine now, I'm probably going to just leave well enough alone.  But if I have to change versions again your post will come in handy, thanks!

---

