---
title: "Windows share"
date: 2017-11-27
forum: General Help
---

### Post by daley.tommeleyn on 2017-11-27
Hey guys,
I got a problem with my ubuntu 16.04 mate. 
i got a windows share( at ip 192.168.0.201) I can't reach... actually I can't reach it at all... my other( windows) laptop I can reach, tho the settings are the same. 
I have tried all the solutions on the forum and on google... 
i even put up a windows virtual machine on ubuntu to see if i can reach it from there, and that works... 
i put up a share on the ubuntu machine and from the windows computer i can reach it... 

so i can reach the ubuntu desktop from all devices, and i can reach all devices from the ubuntu desktop except the one i need. 

Can someone plz help me out because i really don't know what to do any more. 

I'll put up some pictures of the error messages. 

thx in advance!

---

### Post by dragonfly41 on 2017-11-28
I am currently in Windows 10 (I hop between Windows 10 and Ubuntu 16.04 in dual boot).
I did look at setting up Windows Share but found I had to install samba etc.
I took the route of creating a dedicated NTFS partition (/dev/sda9) in unallocated space which I named SHARE.
In Ubuntu I found that I had to install ntfsfix and on each boot up run the command ...

```
sudo ntfsfix /dev/sda9
```
to allow mounting the SHARE partition. 

Now I share data between Windows and Ubuntu.

This is really a work around and does not answer why you can't get it to work using Windows share.

---

### Post by daley.tommeleyn on 2017-11-28
Yes but i want to acces the windows share on 192.168.0.201... not on the same computer...

I also don’t have space to create ntfs partition

Plus if my the windows share of my laptop works, why not the windows share of my desktop?

---

