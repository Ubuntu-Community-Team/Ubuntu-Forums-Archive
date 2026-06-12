---
title: "Update error related to gnome-themes input output"
date: 2008-05-14
forum: General Help
---

### Post by oberton on 2008-05-14
Hi
I ran update manager, 61 updates to do and got an error message :

E: /var/cache/apt/archives/mount_2.13.1-5ubuntu2_i386.deb: failed in buffer_read(fd)

I then ran it in console after doing just in case:
sudo apt-get clean
sudo apt-get autoclean

and got the following:

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/mount_2.13.1-5ubuntu2_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `gnome-themes': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/mount_2.13.1-5ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Its probably something to do with gnome-themes but I am stuck and will probably reinstall unless somebody can help.

Thanks

---

### Post by oberton on 2008-05-14
Anybody on that?
Am I in the right section of the forum or would you be able to point me to another source of info?
Thanks

---

### Post by oberton on 2008-05-14
Allright I guess I will reinstall since all I could find on the web that was close to my issue ended up in a reintalation :(

---

### Post by rubicon on 2008-05-14
```

sudo rm /var/cache/apt/archives/mount_2.13.1-5ubuntu2_i386.deb
sudo apt-get update
sudo apt-get upgrade

```
BTW, for yours own sake, don't just run it, better find out what these commands mean, it will give you more experience with system administration. And &#8212; I hope this helps.

---

### Post by oberton on 2008-05-14
Thanks but I have tried those already and got the same error message as the one I pasted up there....

I dont know much Linux but I have been working in IT for a while so I am OK doing command lines etc.. (I did work on AS/400 15 years ago so thats was a good CLI training :) )

---

### Post by rubicon on 2008-05-14
Have you checked your files like mentioned here: [http://exain.wordpress.com/2007/12/03/failed-in-buffer_readfd-on-ubuntu/](http://exain.wordpress.com/2007/12/03/failed-in-buffer_readfd-on-ubuntu/) ?

It seems to be like similar problem got solved there.

---

### Post by oberton on 2008-05-14
thanks, intresting post but my issue is not related to this particualr package mentionned in my question, any of the 61 updates that I try to perform fails with the same error message about gnome-themes io error, hence my conclusion that it is related to gnome-themes package dependencies problems.

This is right now where my troubleshooting skills stop...if I knew more about Linux I would probably uninstall / reinstall the gnome-themes but since its the desktop you probably cant do that in the GUI and I am affraid I will break something else so I see a reinstall in my near future :)

---

### Post by oberton on 2008-05-14
Sorry ingnore my last post: I read in more details what you sent and the file list (gnome-themes.list) might well be my issue...I will try this later on and let you know even though in the post you mentionned the guy had another debian install where he could copy back the .list file and I dont have that so I have to reconstruct it somehow..should be interresting!

---

