---
title: "Wubi noob question !"
date: 2008-02-27
forum: General Help
---

### Post by quecoder on 2008-02-27
hello , I liked the way Wubi installs ubunto ..I needed something like it because my CD burner is malfunctioned i don't know why ..anyway , I preferred to ask before trying to do anything with Wubi ... 
*Do I have to let Wubi downloads an ISO from the internet , although I have an ISO on my hard disc  and my internet connection is slow ?
*Do I only need to run the installer and let it installs the ubunto for me ..?? 
* is there any detailed instructions of the installation process , I read some from the Wubi website , but it's so brief !!!! 
please help me , i want to use ubunto but really am very NOOOB( i'm afraid this day will not come:( )

---

### Post by ago on 2008-02-27
> **quecoder said:**
>  
*Do I have to let Wubi downloads an ISO from the internet , although I have an ISO on my hard disc  and my internet connection is slow ?
Just put the ISO in the same folder of wubi.exe. Make sure it is the right ISO though!!!
Wubi 7.04 requires the ALTERNATE ISO, Wubi 8.04 requires the DESKTOP ISO (alpha5+)

> *Do I only need to run the installer and let it installs the ubunto for me ..??
As opposed to...? 

> * is there any detailed instructions of the installation process , I read some from the Wubi website , but it's so brief !!!!

[img]http://wubi-installer.org/images/wubi-123.jpg[/img]



I bet they told you linux is difficult... :D

---

### Post by quecoder on 2008-02-27
hi , Ago! ... are these the only steps I need to follow to get it installed !! really ?? I can not believe :)
* I have free space on drive C ( NTFS 9GB free) .. can I choose using this drive !? and what if , windows was infected and I need to re-install it ? the ubunto will be removed ? 
* this is not like LIVE CD that runs from within windows? I mean , is it a real installation of ubunto ?
Thanks alot !

---

### Post by quecoder on 2008-02-27
well i'm downloading the alternate CD ,, it's name is **ubunto-7.10-alternate-i386.iso** ... is this correct ??

---

### Post by ago on 2008-02-27
> **quecoder said:**
> hi , Ago! ... are these the only steps I need to follow to get it installed !! really ?? I can not believe :)
Usually yes.

> * I have free space on drive C ( NTFS 9GB free) .. can I choose using this drive !?
Why not?

> and what if , windows was infected and I need to re-install it ? the ubunto will be removed ?
Easy trick is to backup the /ubuntu dir. Run wubi again to setup the bootloader, then replace the the ubuntu dir with the one backed up.
 
> * this is not like LIVE CD that runs from within windows? I mean , is it a real installation of ubunto ?
Yes it is a real installation (even more so with 8.04). But it is not as robust/performant as a full installation to a dedicated partition. I usually recommend users to use Wubi to play with Ubuntu for a while, then if you like it, do a full installation via CD or LVPM, otherwise uninstall and be happy.

---

### Post by quecoder on 2008-02-27
Thanks alot Ago !

---

