---
title: "failed to download"
date: 2015-05-15
forum: General Help
---

### Post by hmiersch on 2015-05-15
for the last few days i haven't been able to update my system. when i run the software updater, it tells me it's gonna download a certain amount (today it was 3.2 MB or something) and then i click install, it downloads some stuff, then it tells me it "failed to download package" or something. if i then run the software updater again, it tells me 6 KB (down from 3.2 MB) will be downloaded, but then that download fails again.

so what is this 6 KB file, and why does it consistently fail to download?

---

### Post by dino99 on 2015-05-15
do update & upgrade from a terminal, and see the output to know if something is broken
> sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade

---

### Post by hmiersch on 2015-05-15
I tried sudo apt-get update, and it sucked down some stuff but I don't remember seeing any error messages. when I get home I'll try the other commands. Lets see what comes up...

---

### Post by hmiersch on 2015-05-16
today i tried the software updater again. this time it told me it would download a couple hundred KB but again it "failed to download. so i dug a little deeper, and it turns out the culprits are the "GNOME control center account plugins for single sign-on" for facebook, twitter and flickr, 3 kb each. so one of them is ok but the other 2 have problems. 

so the question is, why should i download them? why are they even installed? i'm not on facebook, i'm not on twitter, and i'm not on flickr either, so what's the point? how do i remove them?

---

### Post by mrcpuhead on 2015-08-14
The command line method worked fine, though it doesn't explain why the gui software updater failed to download updates. I would think it would be designed to do the fix command if it runs into problems.

---

### Post by hmiersch on 2015-08-16
whatever the problem was, it was fixed at the other end. after some time the whole process returned to normal.

---

### Post by kiraq on 2015-08-16
Every once in a while, the updater has a broken link or the update hasn't been placed yet. I've had times where I would download one update at a time till I hit the one that wouldn't download, and then bypass that one. I've noticed several times in the past where one bad link would prevent any update from downloading. Thankfully, it doesn't happen often.

---

### Post by newcfd on 2015-08-16
do 
sudo apt-get autoclean
sudo apt-get autoremove
then 
sudo apt-get update

---

