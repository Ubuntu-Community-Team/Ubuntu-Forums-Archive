---
title: "LiveCD Ubuntu Wine? Is it possible?"
date: 2008-06-25
forum: General Help
---

### Post by ech0419 on 2008-06-25
If you read some of my other posts.. basically I have a hard drive that the partition table had failed on. I want to at least attempt to recover the data or bring the partition back so I can use the hard drive. 

So, I'm running a liveCD (6.10 Edgy) and the program is for windows, is it possible to install wine on a LiveCD? and the partition is NTFS would that cause any problems even if it's running through wine?

Thanks.

---

### Post by dracayr on 2008-06-25
I don't really understand why you want to run wine... If you want to recover data, you don't need wine for that...


dracayr

---

### Post by jualin on 2008-06-25
to answer your question yes, it is possible to install almost anything on a live CD. If your program works on Wine then you can install Wine with the Live CD, However you need an internet connection.

---

### Post by WRDN on 2008-06-25
Remember also that, when using a Live CD, everything is placed in the RAM, including installed programs, so if you don't have much to begin with, don't try installing programs.

---

### Post by ech0419 on 2008-06-25
Ok, I was unsure of how it works exactly. I have 1gb of ram as well which it only uses about 600mb of. 

If you don't mind could you walk me through installing it? I always liked linux but never used a program that wasn't included in the CD.

*edit* dracayr** I want to use a recovery tool for NTFS volumes, it is a free windows application. I want to recover the NTFS table on the hard drive. It failed due to a short from my power supply.

---

### Post by Taxman415a on 2008-06-25
You're probably going to want to download a new 8.04 livecd so that you can get a more up to date version of wine, but if you can't so be it. Basically you just boot the livecd and install programs like you would if you were running a full system. They'll just be gone when you reboot. So go to Applications then Add/Remove then search for wine and install it. Then you'll need to copy the installer for your windows application  to your Ubuntu environment, say to the desktop for example. Then open a terminal from Applications --> Accessories and type 'cd Desktop' then 'wine installerblah.exe' will install the application. If all goes well it will be able to work. Not all applications work with wine. If this one does't work with the version of wine that comes with edgy, then you can either try to get a newer ubuntu and wine version or try some other recovery methods.

---

### Post by cariboo on 2008-06-25
If you want to do data recovery using Ubunutu, it might be better to go here:

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

Download and burn the iso, then follow the instructions on the page.

Jim

---

### Post by Taxman415a on 2008-06-25
ubuntu rescue remix is a good idea. They also have the packages needed to install to get the functionality on the bottom of this page: [http://ubuntu-rescue-remix.org/Software](http://ubuntu-rescue-remix.org/Software) (just remove the extra sudo). Of course these are command line tools and they may not be ech0419's cup of tea, but I agree it is a good alternate route.

---

### Post by ech0419 on 2008-06-25
Ok thanks. I can't really get another liveCD I don't have any way to.

I'll see if I can get wine working. 

cariboo907* Would it work on NTFS partitions? I always though ubuntu had a lot of problems with it. It's more of partition table failing then data loss, everything is there it just doesn't have a clue as to how to mount the nothing of a file system it has.

---

### Post by Taxman415a on 2008-06-25
The NTFS tools are much better than they used to be. Not foolproof, but neither are the NTFS tools that come with Windows. That's another reason to get the newer version of Ubuntu, so you get the latest ntfs tools. Try using a friend's computer or something.

---

### Post by ech0419 on 2008-06-25
I'll try my friend and his brother have a couple gaming rigs but I doubt they'll let me crack open a $2,500 computer to pop in my hard drive. I'll see if I can get him to download the newest liveCD. I couldn't find it on demonoid, where could I find a bittorrent download of it?

---

### Post by Elfy on 2008-06-25
There is a torrent here

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

---

### Post by ech0419 on 2008-06-25
Thanks, I'll have him download it for me.

---

