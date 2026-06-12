---
title: "Java[Solved]"
date: 2007-10-23
forum: General Help
---

### Post by M4rotku on 2007-10-23
Hey guys, if I sound like a noob, well, this is my first post, so duh :confused:

Thanks in advance for the help.

I can't seem to download java or any sort onto my firefox.  I tried using the sun whatever's homepage and installing from there, but I am a noob, and the directions were really complicated (from my point of view).

Can anyone point me towards the right website/give me really, really easy steps to installing some Java because I'm going crazy without my games :lolflag:

Thanks.

---

### Post by Maestro23 on 2007-10-23
Open up Synaptic, search for java6.  Install

---

### Post by Bablefish on 2007-10-23
It's even in Add/Remove

---

### Post by M4rotku on 2007-10-23
What is synaptic, i'm sorry, but i'm a [SIZE="4"][COLOR="DarkOrange"]huge[/COLOR][/SIZE] noob and have no clue what that is even.

Can you water the directions down to individual mouse clicks?

---

### Post by Maestro23 on 2007-10-23
> **M4rotku said:**
> What is synaptic, i'm sorry, but i'm a [SIZE="4"][COLOR="DarkOrange"]huge[/COLOR][/SIZE] noob and have no clue what that is even.

Can you water the directions down to individual mouse clicks?

System>> Admin>> Synaptic

Some links for future reference:

Installing Software in Ubuntu:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by M4rotku on 2007-10-23
Ok, so i got to synaptic and an error occured when i tried to open it.  It said:  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  E: _cache->open() failed, please report.

And now I am even more confused :(

---

### Post by M4rotku on 2007-10-23
bump?

---

### Post by Maestro23 on 2007-10-23
> **M4rotku said:**
> Ok, so i got to synaptic and an error occured when i tried to open it.  It said:  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  E: _cache->open() failed, please report.

And now I am even more confused :(

Run the command as stated:

> sudo dpkg --configure -a

Then** [B]sudo apt-get update**[/B]

Try installing the java again thru Synaptic.

---

### Post by kentl on 2007-10-23
sudo apt-get update

---

### Post by M4rotku on 2007-10-24
It says that Java downloaded successfully, but when i try to get on [color="red"]Runescape[/color], the website still tells me that i have missing add ons.

---

### Post by M4rotku on 2007-10-24
Never mind, it works, thanks guys :)

---

### Post by Maestro23 on 2007-10-24
> **M4rotku said:**
> Never mind, it works, thanks guys :)

Glad you got it going.  Please mark this SOLVED using the Thread Tools.

Thanks.:)

---

### Post by mig5 on 2007-11-02
As a side note, you may want to consider doing the following to stop runescape loading from scratch every time you play:
Make a folder in /home/[username]/ called .file_store_32 and another called .jagex_cache_32 . Once you've done that make sure you are selecting 'signed applet with default java' on the runescape detail select screen, and the game should load much quicker.

---

### Post by stchman on 2007-11-02
> **M4rotku said:**
> Hey guys, if I sound like a noob, well, this is my first post, so duh :confused:

Thanks in advance for the help.

I can't seem to download java or any sort onto my firefox.  I tried using the sun whatever's homepage and installing from there, but I am a noob, and the directions were really complicated (from my point of view).

Can anyone point me towards the right website/give me really, really easy steps to installing some Java because I'm going crazy without my games :lolflag:

Thanks.

Here you go:

```
sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-jdk sun-java5-fonts sun-java5-plugin
```

This will fix you up.

---

### Post by Sef on 2007-11-02
> sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-jdk sun-java5-fonts sun-java5-plugin

That is the old version of Java.  Update 6 is the latest version and it is the one to be used.  Also using Add/Remove is much simpler.

---

