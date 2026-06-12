---
title: "Remastersys problem"
date: 2008-03-20
forum: General Help
---

### Post by coninsan on 2008-03-20
Hi

currently i am trying to make a backup of my pc before i resize my partition.
But when i try to boot of the live cd i get this error mesage.

Kernel image corrupted or missing. 

it is not 100% correct, it is just what i can remember, but ive tried 2 times to make a working live cd, i get this error every time.
Am i doing something wrong with remastersys since im getting this error? :confused:

---

### Post by fela on 2008-03-20
download another livecd iso off cdimage.ubuntu.com, this time after it's downloaded verify it's md5 checksum ($ md5sum <filename>) with the one on cdimage.ubuntu.com. If it's exactly the same, your file isn't corrupt, and should work as a LiveCD once you burn it to a disk. good luck :)

---

### Post by coninsan on 2008-03-20
its not the ubuntu live cd that is corrupt, i have a working one that is just fine.
the problem is when i try to make a personal live cd, with My system on it as a backup.
i use remastersys to do it but somehow the kernel in the live cd remastersys makes is corrupt and does not work.

---

### Post by impresionist on 2008-06-03
Hello all,
I think that I have the same problem, within I spend several hours, or days, but no solution yet...
My problem had been started when I install the virtual box, remastersys, evry time make me live-costum.iso.md5 no way to get the .iso file...
I traid to make a distro, it's work, and all ok, but complete backup, I mean with home files, no way, always I get the md5...:mad:
I try to make it in remastersys own program, and through root terminal, in this one the last line which I get, that: ls can't access to the directory 
/home/remastersys/remastersys/custom-live.iso: file not exist


Any solution?
I'll be really thanks in advance...

---

### Post by simurg56 on 2008-06-11
I have the same problem too. but, yes distro option works well..

---

### Post by darthchaosofrspw on 2008-06-16
> **simurg56 said:**
> I have the same problem too. but, yes distro option works well..

The only way I can get the dist option to work in Xubuntu is add a remastersys group in Applications -> System -> Users and Groups and add root and my user(s) to the remastersys group, reboot, log back in, and then I can use "sudo su" then "remastersys dist". BTW I have Remastersys 2.0.5 installed. Over the past two days I've used "remastersys dist" to create customized versions of gOS Rocket E (gOS Ultimate E) and Xubuntu 7.10 (Xubuntu Xtreme 7.10). I've put download links on my blog, [http://darthchaosofrspw.wordpress.com](http://darthchaosofrspw.wordpress.com)

---

