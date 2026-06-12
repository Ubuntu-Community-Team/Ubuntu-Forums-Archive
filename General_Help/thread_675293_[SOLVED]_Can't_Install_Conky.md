---
title: "[SOLVED] Can't Install Conky"
date: 2008-01-22
forum: General Help
---

### Post by Derspankster on 2008-01-22
I've been trying to install Conky and can't. When I run sudo apt-get install conky I get the following error;

E: Couldn't find package conky

My guess is either I don't have the correct repository enabled but have no idea what it should be. I can't find Conky in Synaptic either.

EDIT: I run 7.10 with Compiz

---

### Post by spupy on 2008-01-22
Try
```
sudo apt-cache search conky
```
to check if it is the repos you have.

---

### Post by Derspankster on 2008-01-22
> **spupy said:**
> Try
```
sudo apt-cache search conky
```
to check if it is the repos you have.

I get no return from that command, so apparently not.

---

### Post by spupy on 2008-01-22
> **Derspankster said:**
> I get no return from that command, so apparently not.
(Not sure how helpful this will be since i don't have Ubuntu right now)
But i think you are missing some lines in sources.list
```
cat /etc/apt/source.list
```
In this file the respositories are listed. 
You should have something like this (pretty messy):
[http://tuxicity.wordpress.com/sourceslist-for-gutsy-gibbon/]("http://tuxicity.wordpress.com/sourceslist-for-gutsy-gibbon/")
They might be commented.
```
sudo gedit /etc/apt/sources.list
```
to edit the file.
Better ask someone for the default sources.list file.

---

### Post by Derspankster on 2008-01-23
I did have a problem with my repositories. I took a look at the repositories on my laptop which also runs 7.10 and found a difference in the main repo line. I have no clue how the line was changed on my desktop system but I fixed it and was able to download conky. Thanks! Now, I've got to set out to configure conky.

---

