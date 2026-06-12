---
title: "Switching Laptops"
date: 2006-11-29
forum: General Help
---

### Post by Absolom on 2006-11-29
Hello I'm running Ubuntu 6.10 on my Compaq Presario R3000 and love it but just bought new laptop which is arriving Mon a new Dell Inspirion 6400 What I'd like to know is the best way to migrate all my stuff over to the new laptop   I was thinking I'd do Fresh install on new one and move my directory over to it but not sure about moving all system settings and such
Not sure all the dirs that contain like what is installed besides my home directory..

Or is there a simpler way I figured since is completely different computer wouldn't be good to just duplicate everything since I'm sure many drivers etc will be different..

---

### Post by madmetal on 2006-11-29
i suggest make a clean install and then export settings from the old one and syncronise it with the new one..
and copy paste files then..
it will take more time but it will be better and more safe..

---

### Post by strabes on 2006-11-29
copying home dir will do most of your settings, firefox extensions, etc. Then when you reinstall all the programs their settings will be saved. You might have permissions problems with it though so you could just do a ```
sudo chown -R yourusername /home/yourusername
``` after you copy it over onto the new system.

---

### Post by brottman on 2006-11-29
> **strabes said:**
> copying home dir will do most of your settings, firefox extensions, etc. Then when you reinstall all the programs their settings will be saved. You might have permissions problems with it though so you could just do a ```
sudo chown -R yourusername /home/yourusername
```

I agree this is the best route. I have a seperate partition on my hard drive that I tell the installer to mount for /home, so that when I install/reinstall a new version of Ubuntu, nearly everything is there as soon as I log in.

---

### Post by kylevan on 2006-11-29
> **brottman said:**
> I agree this is the best route. I have a seperate partition on my hard drive that I tell the installer to mount for /home, so that when I install/reinstall a new version of Ubuntu, nearly everything is there as soon as I log in.

all hail the separate /home partition!

it's a really good idea, one of the first things about Linux (Unices in general, I guess,) that I thought "wow, that's really smart," while I was learning the basics of Linux a few years ago.

---

### Post by Absolom on 2006-11-30
I was planning on copying home dir to cd then copying it over mine on new comp but just had idea if after fresh install on new comp can I plug both into my router and transfger stuff directly from 1 to the other? or is that making things unnecessarily complicated?

I like that idea of home being on it's own partition I may do that on the new comp.... how big should I leave for system and what for the home?

---

