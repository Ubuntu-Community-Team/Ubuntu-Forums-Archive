---
title: "Bittorrent Crashing"
date: 2008-04-17
forum: General Help
---

### Post by shmoe010 on 2008-04-17
I am trying to get a file over Bittorrent and I am getting the following error:

[Errno 24] Too many open files.

I have tried some solutions I found (editing the /etc/security/limits.conf file) but to no avail.

If anyone has a solution it would be greatly appreciated!

---

### Post by daengbo on 2008-04-17
Which client are you using? What are your preference for the client set at?

---

### Post by shmoe010 on 2008-04-17
I'm using 'bittorrent' that came with ubuntu (I'm a new user.)

I prefer Azureus but whenever I start that up in just closes itself up. And I can't seem to find how to get to the preferences of the standard bittorrent client.

---

### Post by Tomatz on 2008-04-17
In a terminal:

```
sudo apt-get install azureus
```

Azureus is far superior to the "bog standard" bittorrent and it downloads much faster. ;)

---

### Post by Tomatz on 2008-04-17
Duh sorry didn't read correctly.

Try this in a terminal to get azureus working:
```

sudo apt-get install sun-java6-jre

then

sudo update-java-alternatives --auto
```

This should get azureus working ;)

---

### Post by zvacet on 2008-04-17
You can also try Deluge,Ktorrent,Transmission and see which one you like best.

---

### Post by danwood76 on 2008-04-17
Azureus for the win! ;)

---

### Post by hyper_ch on 2008-04-17
I'd go for rtorrent ;) ncruses based client, very light, very powerful...

---

### Post by shmoe010 on 2008-04-17
> **Tomatz said:**
> Duh sorry didn't read correctly.

Try this in a terminal to get azureus working:
```

sudo apt-get install sun-java6-jre

then

sudo update-java-alternatives --auto
```

This should get azureus working ;)

I ran those commands, and the first one told me "0 updates 0 replaced" and the other just said "no alternatives" over and over.

The problem is that when I open Azureus I see that Welcome thing (where it asks what language you want it to be in) but then before I can even click "next" it just closes...

---

### Post by TheLions on 2008-04-17
> **danwood76 said:**
> Azureus for the win! ;)

+1 fo Azureus

---

### Post by danwood76 on 2008-04-17
Try running azureus from the terminal.
It will probably give a message as to why its crashing.

It could be an incorrect java version or something.
Have you tried downloading the latest version of azureus from their site?

---

### Post by shmoe010 on 2008-04-17
> **danwood76 said:**
> Try running azureus from the terminal.
It will probably give a message as to why its crashing.

It could be an incorrect java version or something.
Have you tried downloading the latest version of azureus from their site?

This is the error from the terminal:

```
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb454474b, pid=6784, tid=3084159888
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0xb74b]

```

---

### Post by Tomatz on 2008-04-18
Either try the latest version of azureus from their site.

or

```
sudo apt-get install ktorrent
```

Ktorrent is quite good also ;)

---

### Post by hyper_ch on 2008-04-18
> **Tomatz said:**
> Either try the latest version of azureus from their site.

or

```
sudo apt-get install ktorrent
```

Ktorrent is quite good also ;)

kTorrent is good... used it also before I discovered rTorrent :)

---

### Post by NightwishFan on 2008-04-18
Ktorrent is my favorite client, I used to use it in Gnome even. Azureus Vuze annoys me, so I dropped it entirely. Transmission is ok, but simple, which is good for some.

---

### Post by danwood76 on 2008-04-18
Vuse is rubbish but you can turn it off and just have the classic azureus interface (v2 style).

---

### Post by Washer on 2008-04-18
get the newest azureus, if you need instructions look at my post history

---

