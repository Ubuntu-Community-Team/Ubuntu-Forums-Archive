---
title: "Problem installing, 256 MB of RAM"
date: 2013-07-14
forum: General Help
---

### Post by Alship on 2013-07-14
Hello all, I come to you with a problem that seems easy but for the life of me no matter what I do it doesn't work.

I've tried 3 distro's to see if any of them work out of Mint Lubuntu and Puppy, Puppy is the only one to start.


Someone I know that I was talking to on Facebook said to try edit the boot parameters to add "xforcevesa" and "nomodeset" both of these failed. They both lead to a blank screen with nothing on them. However when I get into Puppy it takes less than 10 minutes in-fact less than 5 minutes. So I am currently talking from my laptop where as I want to install Lubuntu on my old desktop, does anyone have any ideas as to what could be wrong or anything that would stop it? I've tried installing and it hangs on the blank screen, the same with live mode. I can't even use CTRL + ALT + F1 - F6. I've also tried removing the splash screen, but that doesn't solve much it does take awhile generating the locales for EN, and the syscall but it gets past them with no errors that I can see, after which it just sits at the black screen. It varies in time it takes to get to the blank screen so sorry if it takes awhile to get the results from something.




I don't know the full specs since there is currently no OS on it but what I know is:

30GB HDD
2.6Ghz Processor (Pentium I think)
256 MB of RAM.


It used to "run" XP but I thought why not Linux since it is getting old and has no access to internet so I just want a lightweight distro so I can work on some simple Python apps while reading tutorials on my laptop. But this is proving to be way more of a challenge than I thought. Any help would be greatly appreciated.

---

### Post by kc1di on 2013-07-14
Which version of Lubuntu are you trying to install?  
if it's 13.04 then I would try 12.04.  Lubuntu does not have any LTS but a group has done LTS for it it's call LXLE 
you can get it from[ here.]("http://distrowatch.com/table.php?distribution=lxle")

12.10 and 13.04 use the 3.8 kernel and I've found it does not play well with some video cards.  Also Mint 15 uses that kernel. 

give LXLE a try if you can. I believe it uses 3.2 kernel which is the same series that Puppy uses.

---

### Post by DrScum on 2013-07-14
Try to install 12.04 from the ALTERNATE INSTALL CD which you can find here [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) scroll a little further down and download "PC (Intel x86) alternate install CD" after the system runs you can install the LXDE desktop which turns the "normal" Ubuntu into Lubuntu.

---

### Post by Alship on 2013-07-14
> **kc1di said:**
> Which version of Lubuntu are you trying to install?  
if it's 13.04 then I would try 12.04.  Lubuntu does not have any LTS but a group has done LTS for it it's call LXLE 
you can get it from[ here.]("http://distrowatch.com/table.php?distribution=lxle")

12.10 and 13.04 use the 3.8 kernel and I've found it does not play well with some video cards.  Also Mint 15 uses that kernel. 

give LXLE a try if you can. I believe it uses 3.2 kernel which is the same series that Puppy uses.


Thanks for the help yes it was 13.04, I will try LXLE and report back if anything changes. Thanks.

---

### Post by Alship on 2013-07-14
LXLE boots to a GUI installer it lets me click any and everything but when I choose the hard drive to install on it crashes saying all this text then down the bottom "[OSErrno 12] Cannot allocate memory

---

### Post by Rex Bouwense on 2013-07-14
Although you are within the minimum RAM, it has been my experience that 256 Mbs is sometimes not enough.  I put in another 256 Mb chip in my old Dell Inspiron 1000 (which was also built to run Microsoft Windows XP) and installed Lubuntu 12.04 on it.  It has been running fine.  What you are trying to install now is based on Lubuntu 12.04.

---

### Post by Alship on 2013-07-14
> **Rex Bouwense said:**
> Although you are within the minimum RAM, it has been my experience that 256 Mbs is sometimes not enough.  I put in another 256 Mb chip in my old Dell Inspiron 1000 (which was also built to run Microsoft Windows XP) and installed Lubuntu 12.04 on it.  It has been running fine.  What you are trying to install now is based on Lubuntu 12.04.

Sadly my current situation doesn't really allow me to add more RAM. One of the slots are fried and the working one doesn't seem stable enough to be removed without being broken. Is there any work around for this or is most if not all hope lost on getting it working?

---

### Post by Rex Bouwense on 2013-07-14
You can try the alternate installer.  See here for guidance
[https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall)
Good luck.

---

### Post by Alship on 2013-07-14
> **Rex Bouwense said:**
> You can try the alternate installer.  See here for guidance
[https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall)
Good luck.
Thank you for the help, I will download and write this to a USB, and try it in the morning (4am here) and will report back if any issues are still present.

---

### Post by Alship on 2013-07-15
So, the installation for the alternate install went through fine no errors, but now when I rebooted it goes through fine then my moniter says "Out of range" flipping between that and the cursor on the center of the screen. I've tried pressing CTRL + ALT F1-F6 but it still just loops between it.

---

### Post by Alship on 2013-07-15
It still hasn't got past it, it got past it enough to let me know I had VGA SiS drivers from the help of a friend but since then I haven't managed to get any further

---

### Post by kalehrl on 2013-07-15
Try mini.iso installation choosing command line install.
I had a laptop with 256MB of RAM and that's how I installed Lubuntu on it.
Graphical installation always failed.

---

### Post by Alship on 2013-07-16
I have mentioned the computer doesn't have ineternet access at the current moment. Would that impact it?

---

### Post by tgalati4 on 2013-07-16
Make sure you have a swap partition defined.  That will sometimes help get around the 256MB RAM limitation, both for installation and for running.  Otherwise, you may have to play around with the graphics settings to get around the auto-detection and force a native resolution.

---

### Post by kalehrl on 2013-07-16
>  Would that impact it? 				
Yes, for mini.iso installation you need to have internet access.

---

### Post by mörgæs on 2013-07-16
I wouldn't waste more time on this old fella. If you can't add memory beyond 256 MB it will not be usable for browsing the web, watching a film, playing Flash, ... 

Used (but a little younger) hardware is so cheap that there is no point in keeping it.

---

