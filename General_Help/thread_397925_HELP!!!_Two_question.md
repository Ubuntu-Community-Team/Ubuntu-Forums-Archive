---
title: "HELP!!! Two question"
date: 2007-03-31
forum: General Help
---

### Post by honorshark on 2007-03-31
Hi! I want to ask you for help! I have a problem. I've installed Ubuntu because my friend preferred it, and I like it very much. Stable, fast, good-looking. I have just one "question" (or two).

First: How can I switch a boot logo (the ubuntu logo with orange load bar) to a detailed one... i give a link what I mean...  [http://youtube.com/watch?v=JDhTSUZTBFU]("http://youtube.com/watch?v=JDhTSUZTBFU")

If this function is old don't think about it...

The second one... How can I change GNOME to the "MACOSX" looks.. you know.. the bar at the top or at the bottom... I don't know this but I always using google....

I've installed these linuxes (and used): openSUSE 10.1,10.2 (lot time), Fedora Core 6, Kubuntu x86_64

(One more... how can I play with my Source (STEAM) games with Cedega on Ubuntu??? IT always come with a very small screen at the top-left and it die.... please help!)

Thanks!!!

---

### Post by SendDerek on 2007-03-31
First:  I don't know.  But, I do remember hearing that 6.06 (Dapper) has the detailed boot and during the upgrade to 6.10 (Edgy), the detailed mode went to something called "silent".  
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)


Second:  There are all kinds of docks here and there.  Avant is one, gnome dock is another, kiba is yet another... just search the forums and you'll find a ton I'm sure.

---

### Post by teaker1s on 2007-03-31
detailed boot is obtained by removing "quiet" from grub config file
```
sudo gedit /boot/grub/menu.lst
```
save file
```
sudo update-grub
```

---

