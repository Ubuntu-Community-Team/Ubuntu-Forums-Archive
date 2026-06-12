---
title: "Wubi Hibernation"
date: 2007-05-08
forum: General Help
---

### Post by jettplane on 2007-05-08
I've been trying to get Wubi to hibernate on my Inspirion 6000 laptop.  I've seen all the posts in other forums about hibernation problems, but none seems to solve  the problem. I can't tell if there is any Wubi issue that may add to the problem.  Any one have any experience getting hiberation with Wubi?

Thanks-

---

### Post by LegoAddict on 2007-05-08
I cannot hibernate either, but that seems like a generic Ubuntu problem.  I wouldn't think Wubi would have anything to do with it.

Not that I know about the inner workings of Wubi or Linux.

---

### Post by ago on 2007-05-08
Make sure the swap.virtual.disk is at least as large as your memory.

---

### Post by jettplane on 2007-05-08
Swap disk is exactly the size of memory.  Would more help?

---

### Post by ago on 2007-05-08
Probably not since the actual memory is compressed during hybernation and in normal use it would require less space than full memory (or at least this is what I recall) . It may well be a general Ubuntu issue, but I have never specifically tested hybernation with Wubi, I will do so in the coming days.

---

### Post by varchar255 on 2007-05-08
> **jettplane said:**
> I've been trying to get Wubi to hibernate on my Inspirion 6000 laptop.  I've seen all the posts in other forums about hibernation problems, but none seems to solve  the problem. I can't tell if there is any Wubi issue that may add to the problem.  Any one have any experience getting hiberation with Wubi?

Thanks-

I also have a Dell Inspiron 6000 and cannot suspend or hibernate using Wubi. I searched the forums and tried every potential fix I saw but nothing helped. Most of those forums were people having trouble *resuming* from suspend/hibernate but my problem is that when I initiate a suspend or hibernate from a running session, the screen goes black with a blinking cursor in the upper-left and the system never turns off (or goes to standby). Ctrl+Alt+F1 through F6 work but I cannot type anything else, and Ctrl+Alt+F7 will give me a black screen and then I cannot switch to any other tty. The only clue I have is when I logged out first, then tried to hibernate, it got stuck on the "Shutting down ALSA" command...I couldn't find any more useful information from there though.

I do run Beryl and Network Manager, but I have tried shutting them down first and uninstalling and it doesn't make any difference.

I'm not sure this is a Wubi problem either but I can't do a real install right now, otherwise I'd try that.

---

### Post by MyR on 2007-05-11
hibernation isn't a general ubuntu problem. it works fine on my dell inspiron 6000 feisty installation

---

### Post by ago on 2007-05-11
Yes I can confirm it is a wubi issue at least on inspiron (I have that too). I have opened this bug [https://bugs.launchpad.net/lupin/+bug/113703](https://bugs.launchpad.net/lupin/+bug/113703)

I will not be able to work on it at the moment. It would be interesting to know if hybernation works in some situations.

---

### Post by MethodOne on 2007-05-21
This is also confirmed on a Compal DL70 laptop.

---

### Post by LegoAddict on 2007-06-04
Okey, so I just uninstalled/reinstalled (with Test3) to make sure that my swap size (1.5 GB) was larger than my RAM (1 GB).  Still no suspending in Ubuntu.  What gives?  It's the one thing keeping me from always booting to Ubuntu.

---

### Post by Gan on 2007-06-06
> **varchar255 said:**
> I also have a Dell Inspiron 6000 and cannot suspend or hibernate using Wubi. I searched the forums and tried every potential fix I saw but nothing helped. Most of those forums were people having trouble *resuming* from suspend/hibernate but my problem is that when I initiate a suspend or hibernate from a running session, the screen goes black with a blinking cursor in the upper-left and the system never turns off (or goes to standby). Ctrl+Alt+F1 through F6 work but I cannot type anything else, and Ctrl+Alt+F7 will give me a black screen and then I cannot switch to any other tty. The only clue I have is when I logged out first, then tried to hibernate, it got stuck on the "Shutting down ALSA" command...I couldn't find any more useful information from there though.

I do run Beryl and Network Manager, but I have tried shutting them down first and uninstalling and it doesn't make any difference.

I'm not sure this is a Wubi problem either but I can't do a real install right now, otherwise I'd try that.
I am using Thinkpad X31 and I have exactly the same symptom as yours. I enlarged the swap to be larger than the RAM and it's still not working.

Actually not just hibernate, I can't even get "Suspend" to be working. Again it stops at a blinking cursor. 

I did full installation of ubuntu a while ago and hibernation worked well then, so I can confirm this is not an ubuntu issue.

---

### Post by macuser9214 on 2007-07-01
anyone get this working?

---

### Post by tuxcantfly on 2007-07-01
One way to get hibernation working (on hardware where it would otherwise work) is to create a real swap partition, and edit fstab to have it use that, though that kind of defeats the purpose of wubi (no repartitioning)...

---

### Post by ago on 2007-07-02
I have asked one of ubuntu kernel developers (mjg59) to have a look at it. So far I had no reply. But it is quite unlikely that hibernation will be made to work any time soon. Suspend might be more manageable and it should already work if you do not need fuse (lubi and wubi on fat32).

---

### Post by porcorosso on 2007-08-16
I was looking for hibernate / suspend features on my system running Wubi/Ubuntu, and then I figured that it wouldn't make much sense to try to support those features in this type of Linux installation. As a matter of fact, there can be issues with using hibernate on an ordinary dual boot configuration, too.

I went to the Wubi site at [http://www.wubi-installer.org/faq.php]("http://www.wubi-installer.org/faq.php") and found this

> Any gotcha?

Hibernation/suspend is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hardreboots (unplugging the power) than a normal filesystem, so try to avoid unplugging the power. These problems, however, are no longer present once the Ubuntu install created by Wubi has been transferred to a dedicated partition using LVPM.

---

### Post by madmatrixz3000 on 2007-09-18
wubi warns about it not working, something in the iso/boot process.  You might be able to go in and fix the code but I don't know

---

