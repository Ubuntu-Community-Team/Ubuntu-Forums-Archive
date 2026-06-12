---
title: "wallpaper changes with restart on hardy"
date: 2008-06-29
forum: General Help
---

### Post by martinoco on 2008-06-29
hi everyone,

absolute newbie here, trying to setup Kubuntu Hardy on my computer. So far everything is going fine, but I'm having a weird problem with my wallpaper: it changes to the default one every time I restart. :confused:
I've searched on the net for some solution but can't find it anywhere. Could any one help me? :(

---

### Post by LunatikOwl on 2008-06-29
I'm not really familiar with KDE but maybe you deleted to picture after you changed the wallpaper?

---

### Post by martinoco on 2008-06-29
> **LunatikOwl said:**
> I'm not really familiar with KDE but maybe you deleted to picture after you changed the wallpaper?

no, that's not the case. It doesn't matter what wallpaper I change it to, when I reboot it's gone.
Thanks for your answer though

---

### Post by martinoco on 2008-07-02
anyone? :confused:

please :(

---

### Post by thetejon on 2008-07-02
I had a similar problem, and it turned out that many of the settings files were owned by root.  I'm using Gnome, so I was in [home folder]/.gconf, and I just changed the owner to be me instead of root, and that took care of the problem.

If you're using Kubuntu, I assume you would be looking in [home folder]/.kde instead.

Anyway, careful changing ownership of files and directories - if you don't know what you're doing here, you might want to at least get someone to second what I'm saying before you try it.

---

### Post by martinoco on 2008-07-05
> **thetejon said:**
> I had a similar problem, and it turned out that many of the settings files were owned by root.  I'm using Gnome, so I was in [home folder]/.gconf, and I just changed the owner to be me instead of root, and that took care of the problem.

If you're using Kubuntu, I assume you would be looking in [home folder]/.kde instead.

Anyway, careful changing ownership of files and directories - if you don't know what you're doing here, you might want to at least get someone to second what I'm saying before you try it.

that's interesting, let's hope someone else confirms it so I don't screw up.
Thanks for the tip :)

---

### Post by rudihawk on 2008-07-05
Your wallpaper could also be stored on a drive that is not automounted when you boot up. Hence the picture is unavaliable. 

How many partitions do you have (if any).

---

### Post by hackerseraph on 2008-07-05
im gonna go with the other partition theory although most of the time when its another partition the wallpaper drops to just a background colour. Make sure you have ntfs support (if you use ntfs) and that the hdd your wallpaper is stored on is mounted at boot.

---

### Post by rudihawk on 2008-07-05
Or just make sure that the wallpaper you would like is on a partition that does get mounted on boot. i.e /home

---

### Post by martinoco on 2008-07-05
thanks for the quick replies, guys :)

rudihawk, I have a single partition. The picutures I want to set as wallpapers are in the /home/ folder, so it seems it's not an mounting issue.
The default wallpaper that sets itself on reboot is on /usr/share/wallpapers/kubuntu-wallpaper.jpg and if I choose another picture on that folder as wallpaper, it sets itself to kubuntu-wallpaper.jpg on restart anyway.

This is a fairly new install. The only software I've downloaded is Amarok stuff (I use the computer as a music player mainly). Specifically, I installed SuperKaramba to get the cd cover on the desktop. Maybe that's causing the problem?

Again, thanks anyway for your help guys.

---

### Post by Zorael on 2008-07-05
I'd wager it's a permissions issue. Try creating a new (temporary) user. Does he/she/it experience the issue as well?

If not, try this in a terminal.
```
$ sudo chown *<user>*:*<group>* ~/.kde -R
```
Obviously, replace <user> and <group> with your username and your usergroup. They are the same per default, unless you've explicitly changed your group.


I don't know how "deep" chown -R goes, but hopefully that should take care of things. If not, do this for good measure.
```
$ for X in `ls -w1 ~/.kde`; do sudo chown *<user>*:*<group>* $X -R; done
```
I'm logged into Windows at the moment (Age of Conan is a "Game for Windows", damn it all), so I can't test the syntax of that for clause, but it should work.

---

### Post by martinoco on 2008-07-06
> **Zorael said:**
> I'd wager it's a permissions issue. Try creating a new (temporary) user. Does he/she/it experience the issue as well?


yep, seems like a permissions issue. I made a new user and it didn't experience the issue.

> 
If not, try this in a terminal.
```
$ sudo chown *<user>*:*<group>* ~/.kde -R
```
Obviously, replace <user> and <group> with your username and your usergroup. They are the same per default, unless you've explicitly changed your group.

I tried that, but it didn't work :(

> 
I don't know how "deep" chown -R goes, but hopefully that should take care of things. If not, do this for good measure.
```
$ for X in `ls -w1 ~/.kde`; do sudo chown *<user>*:*<group>* $X -R; done
```
I'm logged into Windows at the moment (Age of Conan is a "Game for Windows", damn it all), so I can't test the syntax of that for clause, but it should work.

it seems the syntax in that command is wrong and chown refuses to work.
thanks anyway for you help, zorael. I feel we're getting close! :)

---

