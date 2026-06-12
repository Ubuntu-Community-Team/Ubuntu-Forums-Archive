---
title: "alsamixer"
date: 2005-06-01
forum: General Help
---

### Post by Sipheren on 2005-06-01
Hey all...I am just looking for someone to explain how I install alsamixer....I have followed the install guide as far as I can and i cant find anyting that explains it for someone who has not used linux before....it just says this to install:

Download source codes, then

tar xvfz AlsaMixer.app-0.1.tar.gz
cd AlsaMixer.app-0.1
make
make install-x11

First line worked...but the second ones didnt do anything when I typed them in....

---

### Post by bored2k on 2005-06-01
Applications > System Tools > Terminal
sudo apt-get install alsamixer

In that case, it's
./configure
make
sudo make install

---

### Post by Sipheren on 2005-06-01
thx...that worked....the sound is stilll really bad...its like it doesnt split it into its 5.1 channles and just playes everything through them all....I have read all about this and alsamixer was ment to make it better....is there any way to split the channles into 5.1?

---

### Post by maximilion on 2008-02-08
sudo apt-get install alsamixer says E: Couldn't find package alsamixer.

The reason I want to install it is because I followed the stick guide in Multimedia & Video and 

aplay -l

shows my card (and all sound works in desktop mode), but

alsamixer

gives "no mixer elems found".


My volume icon at top has a red x, and double clicking it gives "No volume control gstreamer plugins and / or devices found".

But sound works fine in desktop, supertux, and Prefs/Sound has all events set to use USB audio.


Thankful for any help!

---

### Post by kerry_s on 2008-02-08
after you install the mixer run->
sudo alsaconf

reboot

then run-> alsamixer

---

