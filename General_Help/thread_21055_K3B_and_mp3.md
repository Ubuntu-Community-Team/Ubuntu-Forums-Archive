---
title: "K3B and mp3"
date: 2005-03-20
forum: General Help
---

### Post by CyrilleMortreux on 2005-03-20
Hi. After a few apt-get dist-upgrade, I have tried to burn an audio CD from mp3 files. 

It usally works well, but now, k3b tells me it can't do anything right with mp3 files because it don't know how to support that king of files ...

So, I just can't burn an audio CD from mp3 files, I have to convert them to wav before and then k3b can burn them. 

What's wrong ???

---

### Post by CyrilleMortreux on 2005-03-20
I found that here, but no way for me tu use rpm files !!!
Must be a way to get the correct plugin from a Debian package. Anyone for a solution ???

Cyrille




[http://www.ubuntuforums.org/showthread.php?t=21044](http://www.ubuntuforums.org/showthread.php?t=21044)

This is annoying, and a sort of hack to get it to work. VERY annoying. And I'm a linux newb, so this may be unethical or something.

But this is what i did.

step 1:go to [http://rpm.pbone.net/index.php3/sta...3.i386.rpm.html](http://rpm.pbone.net/index.php3/sta...3.i386.rpm.html) and download the RPM there.

step 2: sudo alien -i k3b-mp3-0.11.19-0.lvn.1.3.i386.rpm

step 3: sudo chmod 777 /usr/share/apps/k3b/plugins

step 4: download the mad decoder from [http://cvs-digest.org/index.php?tra...n=1.4&mimetype=](http://cvs-digest.org/index.php?tra...n=1.4&mimetype=)

step 5: cp *filename* /usr/share/apps/k3b/plugins, or just drag and drop it into that directory

Hope this helps anyone who had the same problem as me.

---

### Post by dr.drake on 2006-01-03
install the k3b-mp3 package through Kynaptic/Synaptic ??

---

### Post by fizz on 2006-04-10
isnt in the repo's... least for dapper its not...

---

### Post by lnostdal on 2006-04-24
try libk3b2-mp3

---

### Post by TitusDalwards on 2006-04-24
i have the same problem with GnomeBaker and i found it the solvation by this way:
i have upgraded to gnomebaker 0.4.4 but it isn't worked well so i decrease the program to GnomeBaker 0.3.3 and now everything seems well

---

### Post by pcormack on 2006-05-12
I too was having the same issue

@ lnostdal
cheers i can now burn an audio cd from mp3 using libk3b2-mp3

---

