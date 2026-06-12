---
title: "Making a backup of a home folder directly on DVD's"
date: 2007-07-30
forum: General Help
---

### Post by Amon_Re on 2007-07-30
Does *anyone* know of a software that can make backups of a home folder to dvd's?
I can't find anything that'll just dump everything to CD or DVD, sbackup isn't a solution for me, nor is online backups, and home user backup just makes coasters *sigh*

Any hints are welcome

---

### Post by AlexThomson_NZ on 2007-07-30
Can you not just use gnome-baker or similar to burn a data DVD?

---

### Post by Amon_Re on 2007-07-31
Sofar i haven't had any choice really, and gnomebaker isn't that great neighter, using K3B at the moment, but i'd rather have the computer work for me, and devide the data up automaticly.

My Photos folder alone is 13GB, it's a pain in the *** to have to make data-dvd's manually, i wasted 4 hours on that yesterday and i'm only halfway through all my data.

---

### Post by AlexThomson_NZ on 2007-07-31
What I do is just get an external HD (I use a laptop, otherwise I would probably just get an internal), and sync backups to that.  As you mentioned nowadays DVD probably don't have enough storage to be practicable.

You're right about gnome-baker too, doesn't compare to K3B

---

### Post by Amon_Re on 2007-07-31
> **AlexThomson_NZ said:**
> What I do is just get an external HD (I use a laptop, otherwise I would probably just get an internal), and sync backups to that.  As you mentioned nowadays DVD probably don't have enough storage to be practicable.

You're right about gnome-baker too, doesn't compare to K3B

I have backups on HD's,but i don't trust HD's, see enough of them dying, i don't consider a HD to be a reliable backup medium

---

### Post by malel on 2007-08-01
There is a nice little program called "Home User Backup" which is just what you want.
I got it down through Synaptic and it has a nice Gui which tells you everything it is doing. I use it to backup to and external HDD but it also has provision to send it to a DVD.
Regards:)

---

### Post by Amon_Re on 2007-08-01
> **malel said:**
> There is a nice little program called "Home User Backup" which is just what you want.
I got it down through Synaptic and it has a nice Gui which tells you everything it is doing. I use it to backup to and external HDD but it also has provision to send it to a DVD.
Regards:)

Tried it, it made nice coasters :lolflag:
I'll try it again on my other PC just in case tho

---

### Post by Irihapeti on 2007-08-02
I've had some success using Cedar backup, available either through Synaptic or from Cedar's own website. So far, though, I've only needed to use one DVD for a backup. I'm going to have a look at the option to use more than one disk and see how that goes.

The downside to it is that it's a command line program and you have to set up an XML config file beforehand.

By the way, I've discovered in the past couple of days that more than one program handles DVD+RW better than DVD-RW. Is this information of any use to you?

---

### Post by dragonwings on 2007-08-02
try at your own risk i am just learning this stuff myself



maybe you could 

sudo nautilus

then copy and past it and burn to dvd 
-----------------------------------------------------------------------------


to save entire file system to tgz

sudo su 

cd /

tar cvpzf backup.tgz --exclude=/backup.tgz

burn that to dvd maybe using sudo nautilus to do so as it will be in file system and later copy past to your file system   /



to restore 

with tgz in   /

sudo su

cd /

tar xvpfz backup.tgz -C /

---

### Post by Amon_Re on 2007-08-02
> **Irihapeti said:**
> I've had some success using Cedar backup, available either through Synaptic or from Cedar's own website. So far, though, I've only needed to use one DVD for a backup. I'm going to have a look at the option to use more than one disk and see how that goes.

The downside to it is that it's a command line program and you have to set up an XML config file beforehand.

By the way, I've discovered in the past couple of days that more than one program handles DVD+RW better than DVD-RW. Is this information of any use to you?

I'll try this one too, thx

---

### Post by Amon_Re on 2007-08-02
> **dragonwings said:**
> try at your own risk i am just learning this stuff myself



maybe you could 

sudo nautilus

then copy and past it and burn to dvd 
-----------------------------------------------------------------------------


to save entire file system to tgz

sudo su 

cd /

tar cvpzf backup.tgz --exclude=/backup.tgz

burn that to dvd maybe using sudo nautilus to do so as it will be in file system and later copy past to your file system   /



to restore 

with tgz in   /

sudo su

cd /

tar xvpfz backup.tgz -C /

The problem isn't making the DVD, the problem is making it span multiple DVD's

---

### Post by dragonwings on 2007-08-02
system rescue cd  might be of use to you 

it creates a UDF filesystem on a dvd+rw disc 

whick i think divids stuff into 2000mb partions and uses the udf to put them back togeather when resored 

note i havent had much luck with any thing like this yet but as soon as i sort it i will post a how to for dummies like me to help with the so called linux for human beings lol

---

