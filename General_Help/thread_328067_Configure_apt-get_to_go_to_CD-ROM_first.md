---
title: "Configure apt-get to go to CD-ROM first?"
date: 2006-12-30
forum: General Help
---

### Post by rogblake on 2006-12-30
I'm sure this has been asked before, but after some searching here and via Google I have not come up with the answer.

How can I configure apt-get on Dapper so that when I install a package it looks on the distribution CD first rather than going to the internet? I'm on dialup so it's pretty painful when apt-get wants to download something that is already on the CD.

---

### Post by scrooge_74 on 2006-12-30
i think is sudo apt-get add CDROM

or from Synaptic you can set it up

---

### Post by ajgreeny on 2006-12-30
Just remember that you will need the alternative install CD.  The live/install CD that most people use will not work in this way, I'm afraid, so if you got your CD from shipit, I think it is the live CD, and you may be disappointed.

---

### Post by rogblake on 2006-12-30
Thanks -- I tried "apt-get add CDROM" and just get the error "invalid operation add." However, looking at the other apt commands I saw an "apt-cdrom" which I used to add the distribution CD. The trouble is, even after doing this, apt-get *still* wants to go to the internet to install packages that are on the CD. (I just tried this with apache2, which is definitely on the installation CD.)

I'm working with the server edition of Dapper, so there is no GUI or Synaptic. Is there a modification needed in /etc/apt/sources.list or /etc/apt/apt.conf to make this work?

(What I'm doing is configuring a server that will ultimately be transported to a site with high-speed internet available, but the initial setup is being performed at home where there is only dialup.)

---

### Post by taurus on 2006-12-30
```
sudo apt-cdrom add
sudo aptitude update
```

---

### Post by rogblake on 2006-12-30
> **ajgreeny said:**
> The live/install CD that most people use will not work in this way, ... 

This system was installed using the Dapper 6.0.6.1 server edition CD -- can it be made to work in this manner? (If not I could redo the installation using the "alternative" CD, which I have a copy of also. I've just started on this project so wiping and reinstalling would not be too painful at this point.)

---

### Post by ajgreeny on 2006-12-30
Haven't a clue about the server edition CD, but don't see why you couldn't use the alternate install CD in its place.  Give it a try.

---

