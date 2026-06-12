---
title: "No booting options"
date: 2007-09-23
forum: General Help
---

### Post by Omi23 on 2007-09-23
Hi,
I have installed Wubi and then Ubuntu, but when I went to restart my computer to go in to Ubuntu my computer just goes straight to loading Windows XP, there is no option to go either to Ubuntu or to Windows.

Does this Mean that Ubuntu didn't install correctly?  Or didn't even install at all?

I have tried to go to: control panel>system>advanced>startup and recovery settings, but then a message comes up that says: The C:\boot.ini file can not be opened.   Operating System and Timeout settings can not be changed.

The only option is to click OK. So I do and the Startup and Recovery settings come up and the default operating system and time to display list of operating systems are all grayed out.

Please help!  I have a friend that has Ubuntu and well... It's awesome :)  Plus there is a couple programs that I really really really need that only work in Linux, Thanks.

---

### Post by SpiritIsReality on 2007-09-30
howdy
sorry that no one responded. it happens
I don't know about wubi. says ubuntu is created as a loop mounted partition, also known as an disk image.It says it's in beta which means things aren't always going to work out.
What have you tried since you posted last? Try install from live cd or alternate cd ? I'm hoping so.
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
buds

---

### Post by ado_raul on 2007-10-01
###########################################
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /KERNEL=CXLOGO.EXE
c:\wubildr.mbr="Ubuntu"

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="(Backuped by Changer XP)Microsoft Windows XP Professional" /noexecute=optin /fastdetect
###########################################

this is one of my wubi installs.
look at the boot.ini
u can copy paste it in your boot.ini.

there ar 2 things to be aware:
1: that u have the same multi(0)rdisk(0)partition(1) < that means that windows is intalled in c:
2: locate wubidir.mbr and replace acording to tour needs.

P.S. I've never had your problem. It's gust a sugestion.

---

### Post by ago on 2007-10-01
> **Omi23 said:**
> Hi,
I have installed Wubi and then Ubuntu, but when I went to restart my computer to go in to Ubuntu my computer just goes straight to loading Windows XP, there is no option to go either to Ubuntu or to Windows..

Maybe you have multiple installations and the installer got confused. Check boot.ini, there should be a wubi entry

---

### Post by Isovitis on 2007-10-01
> **ago said:**
> Maybe you have multiple installations and the installer got confused. Check boot.ini, there should be a wubi entry
Hi.

I have the same problem with Omi23. I installed Wubi, restarted my computer and no choice between Ubuntu and Windows existed. I entered Windows automatically.

How can I check boot.ini and where shoud be a wubi entry?

Thanks in advance.

PS: I run Windows Vista Business and I downloaded the 7.04.04 Wubi release.

---

### Post by Omi23 on 2007-10-05
Hey thank you for replying, here is the problem I'm trying to find the boot.ini file, Ago said that i should look for that file to see if Wubi had anything in there. I can't find it anywhere.

I've gone through windows and made sure all of the hidden files will show up but there is still no boot.ini in my one and only C: drive. (There is a desktop.ini in My documents, but that probably does do and help).  Thanks for replying, to those that did.  

I have tried Ubuntu on my computer, It works awesome (My friend has the CD).  I just wanted to duel boot because windows has games.  Is the a duel boot feature that Ubuntu has that I can use without Wubi?  Or is Wubi the only way?

Sorry, I just was occupied with other stuff to come and check if anyone had posted anything. Thanks again.

---

### Post by ago on 2007-10-05
Vista is a separate issue. Use EasyBCD to check your boot entries.

As for XP, boot.ini must be in C:\ or D:\ 

Windows 98 uses config.sys

If you have a custom bootloader than you'll need to change that manually.

---

### Post by Omi23 on 2007-10-06
See thats not my problem.  I have no boot.ini file which makes no sense to me.

I have looked in C:\ and D:\ and made sure all hidden files are showing.

Is there any other place I should look for it?

Should I just try and reinstall with Wubi?

Thanks for any replies.

---

### Post by ago on 2007-10-06
XP does use boot.ini, but I am not sure why you cannot access it.

---

### Post by SpiritIsReality on 2007-10-06
howdy
well I think I found a page that kind hints at the boot.ini files of xp. 
I'd rather learn linux than dos., so rather than learn how to modify xp ntfs files., I'm going back to ubuntu installed on the hard drive and rute2038bug.com/index.html.gz and help.ubuntu.com/7.04/server/c .
But if you're sold on wubi,( nothing wrong with something that's going to make it easier to run ubuntu, but I don't think in this case that it is easier than installing to the hard drive, and be done with it. Come back to dos after you get used to linux, and help out on the wubi project, haha!) then I hope this helps.
[http://vlaurie.com/computers2/Articles/bootini.htm](http://vlaurie.com/computers2/Articles/bootini.htm)
[http://vlaurie.com/computers2/slides/showextensionslide3.htm](http://vlaurie.com/computers2/slides/showextensionslide3.htm)
posted this from xp, trying to find the boot.ini files when I suddenly realized, what the hell am I doing here looking for ntfs files in order to run and learn linux? Well that'll be great for when someone wants to learn how to be a Network Administrator runnin' samba so that micsoft and linux can talk. Nothin wrong with a good talk around the campfire.But hay, I'm on chapter four of rute.! and only got there by skipping over a lot of for me hardparts, which is a good place to be, but hay, I've got to try and gain some ground here! haha!
 but hay!?, what kind of hay is that?
greener pastures
buds

rute users manual
[http://rute.2038bug.com/node7.html.gz](http://rute.2038bug.com/node7.html.gz)
search for boot.ini
[http://www.google.ca/search?hl=en&q=boot.ini+location&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=boot.ini+location&btnG=Google+Search&meta=)
I tried using xp search but couldn't get the dog to look for hidden files. I guess I could have searched help to find out how to do that too, but I wasn't gettin anywhere fast.
happy trails
buds

---

### Post by SpiritIsReality on 2007-10-06
howdy
I was going to edit this in to the post above, then I figured the link deserves a post of it's own at the very least!
[http://ubuntuforums.org/showthread.php?t=566861](http://ubuntuforums.org/showthread.php?t=566861)
the times
buds

---

### Post by Omi23 on 2007-10-07
I just sent a request to get a hotfix from Microsoft, to help me with the no boot.ini file.  

I'll get back to you once I have the hotfix installed

Thanks again for the replies.

---

### Post by SpiritIsReality on 2007-10-07
wow
that's thinkin'! make em earn their oats. way to go.
buds

---

### Post by Omi23 on 2007-10-07
They got back to me but its only for Window Server 2003 32bit, and 64bit.  Not for XP.  Unless, Windows Server equals Xp?

I'm really not sure what to do. I guess I could reinstall Windows, but that the last thing I want to do...

Do you know if I could just go ahead and make a boot.ini file?  And put it in my C:\?

---

### Post by meierfra on 2007-10-07
To edit the XP  boot file:

Right Click on "My Computer" and select "Properties"

Click on the "Advanced Tab"

Click on Settings in the "Start up and Recovery" area.

Click on  Edit.

---

### Post by meierfra on 2007-10-07
To find "boot.ini" you need to uncheck "Hide System Files"  ( in the same place where you choose "Show Hidden Files")

---

### Post by SpiritIsReality on 2007-10-07
> **meierfra said:**
> To edit the XP  boot file:

Right Click on "My Computer" and select "Properties"

Click on the "Advanced Tab"

Click on Settings in the "Start up and Recovery" area.

Click on  Edit.
wow
meierfra ... thanks

buds

---

### Post by SpiritIsReality on 2007-10-07
[http://en.wikipedia.org/wiki/Windows_XP](http://en.wikipedia.org/wiki/Windows_XP)

---

### Post by COF on 2007-10-07
hi
I have the same issue, I've ran thhrough the wubi installer w/o a problem, but now when i boot it goes straight to windows. I'm running XP too.
So I found my boot.ini file and here's what I got:
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu"
any suggestions?
thanks
COF

---

### Post by SpiritIsReality on 2007-10-07
howdy

COF
I suggest you copy and paste that into a brand new thread opening post, to improve your chances of getting help. Is there a Wubi forum? It looks like real interesting stuff, but if I was me I'd install to the hard drive and get on with it. whatever works.
wubi forum here [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)
buds

---

