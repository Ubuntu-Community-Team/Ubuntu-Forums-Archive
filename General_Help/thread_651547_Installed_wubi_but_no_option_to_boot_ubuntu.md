---
title: "Installed wubi but no option to boot ubuntu"
date: 2007-12-27
forum: General Help
---

### Post by travismoore on 2007-12-27
I installed wubi then it told me to restart to boot from linux. so I restarted but all i get is a black screen for a few seconds then windows starts... there is no option to boot ubuntu at all =(

Wubi 7.04 if that helps

---

### Post by ago on 2007-12-27
If you use xp check boot.ini (maybe there is more than one around?). If you use vista have a look with easybcd

---

### Post by travismoore on 2007-12-27
I run xp. Any idea where the boot.ini would be or should i search my whole pc?

there is a boot.ini.backup in c:/windows/pps

Just did a whole search of my C drive and all i found what the boot.ini.backup I listed above

I don't know if that's a good or bad thing ...

---

### Post by travismoore on 2007-12-28
help anyone?

---

### Post by HLA91 on 2007-12-28
I have the same problem on my laptop which runs windows ME and i installed xubuntu can anyone please help me with that? It provides no option to boot xubuntu it just goes straight into windows

---

### Post by Planets on 2007-12-29
[http://ubuntuforums.org/showthread.php?t=627347](http://ubuntuforums.org/showthread.php?t=627347)

---

### Post by travismoore on 2007-12-29
Thanks very much man was starting to wonder if I would ever get help.

I don't quite get step one though download a NEW? iso and installer?

Also easybcd seems to be only for vista? im running xp will that mess it up?

Ok just worked out that my boot.ini is in C:\boot.ini         but it must be hidden or something because I cant see it.

---

### Post by Planets on 2007-12-29
I downloaded a completely new ISO and Wubi installer.

---

### Post by ago on 2007-12-30
boot.ini is under C:\boot.ini
But it is often hidden, so you have to select to show hidden files first.

---

### Post by travismoore on 2008-01-01
I tried to use easybcd and got these errors:
[IMG]http://img229.imageshack.us/img229/3222/problem1iy9.jpg[/IMG]
[IMG]http://img183.imageshack.us/img183/2131/problem2io2.jpg[/IMG]
It appears to be for vista only.

Does anyone know an alternate free boot manager for XP?

---

### Post by ago on 2008-01-02
Yes easybcd is only for vista
for xp look at boot.ini

---

### Post by travismoore on 2008-01-03
This is my boot.ini
```

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr="Ubuntu-Linux"

```

All i get is a black screen for a few seconds on start up and then it boots straight to windows.

---

### Post by ago on 2008-01-04
That looks good to me, it should pause for 15 secs and give you the option to boot windows or linux.

maybe you have another bootloader or you boot using another boot.ini
also check that you have wubildr.mbr and wubildr in c:

---

### Post by travismoore on 2008-01-05
Yes wubildr.mbr and wubildr are in c:

and I don't have any other bootloader that I know of.

Problem is it boots up but all i get is a blank screen for 15 seconds and then windows boots.

My new HDD has just arrived so i think im just going to dual boot. 

Thanks for your time anyway.

---

### Post by 888gavin on 2008-01-06
I am trying to set up Wubi from Windows Vista. It told me to restart the computer to finish the installation, but when I did so nothing happened, it just booted straight back into Windows Vista. I do not have a boot.ini file (whatever it's called) in C:/. So, I right-clicked My Computer then went Properties > Advanced System Settings > Advanced Tab > then under Start-Up and Recovery, I clicked Settings. In the Default Operating System Drop-Down, I see Windows Vista, And Wubi-Ubuntu. What do I do from here to enable the boot menu? Any help is greatly appreciated.

Thanks,

Gavin

---

### Post by travismoore on 2008-01-06
You will have a boot.ini (pertty sure) but its hidden. If your open up my computer and type in the address bar at the top "C:\boot.ini" (without the speech marks). It should open up.

Planets has got it to work with vista as well look at his thread here:
[URL="http://ubuntuforums.org/showthread.php?t=627347"]http://ubuntuforums.org/showthread.php?t=627347
[/URL]

---

### Post by 888gavin on 2008-01-06
I tried entering the address for boot.ini, but it was not there.

Is Planets' method the only way to install Wubi? I've never used EasyBCD before, I'm not even really sure what it does.

Is there anyone who can give me specific directions as to what I should do?

Thanks,

Gavin

---

### Post by travismoore on 2008-01-07
Is Planets' method the only way to install Wubi? I've never used EasyBCD before, I'm not even really sure what it does.

Is there anyone who can give me specific directions as to what I should do?

Thanks,

Gavin

I don't think planet's method is the only way but it is one way which he has got wubi to work with vista.

EasyBCD is a bootloader which is made specificly for vista it will allow you to set it up so you can boot vista and wubi(ubuntu). 

As I have XP I can't give you directions for EasyBCD but I'm sure there is someone who can.

---

### Post by ago on 2008-01-07
> **888gavin said:**
> I am trying to set up Wubi from Windows Vista. It told me to restart the computer to finish the installation, but when I did so nothing happened, it just booted straight back into Windows Vista. I do not have a boot.ini file (whatever it's called) in C:/. So, I right-clicked My Computer then went Properties > Advanced System Settings > Advanced Tab > then under Start-Up and Recovery, I clicked Settings. In the Default Operating System Drop-Down, I see Windows Vista, And Wubi-Ubuntu. What do I do from here to enable the boot menu? Any help is greatly appreciated.

Thanks,

Gavin

Vista does not use boot.ini. Please use easybcd, it basically is a very nice graphical front-end to configure vista boot options. The easybcd author has also helped with wubi development. See [http://neosmart.net/software.php](http://neosmart.net/software.php)

After a wubi installation you should see at least 2 boot options: Vista + Ubuntu-Linux, if you don't something went wrong with wubi.

Check particularly the timeout should be higher than 0 or you will not be shown the vista boot menu., 

Please let me know if you find out the reason.

---

### Post by Baltirow on 2008-01-29
Hi I'm new here, but have run in to an old issue it seems.

Two weeks ago I tried to install Wubi. It installs fine, but the computer hangs when the automatic restart is engaged after the installation is complete.

When I restart again, I do not get any boot options (I do get a message that some settings have changed), the computer simply starts Windows. Also in the following restarts.

Further important details:
- I am using Windows Me (go on and laugh ;) ).
- I did not find any hidden 'boot.ini' file in the root of C:\.
- Obviously EasyBcd does not work as I have this particular OS.
- I had found that one of the wubi files wasn't on the C-drive, but after I CP'd it, still no change.
- Id thave tried this both with Ubuntu and Xubuntu (either 7.04 or 7.10, not sure)

I recently had a complete reformatting of my computer and thought this was the perfect moment to do a  dual-boot trial. Anyone have any bright ideas?

---

### Post by ago on 2008-01-29
Me probably uses a different bootloader mechanism which is not supported. If you manage to chainload into grub it would be the best option.

If you use ME though I would suggest to replace it with a proper Ubuntu installation and then run any needed windows app in wine/emulator. That works well for anything except games.

---

### Post by Baltirow on 2008-01-29
> **ago said:**
> Me probably uses a different bootloader mechanism which is not supported. If you manage to chainload into grub it would be the best option.
Could you please elaborate on that second sentence? I'm still quite the newbie in this field.


> **ago said:**
> If you use ME though I would suggest to replace it with a proper Ubuntu installation and then run any needed windows app in wine/emulator. That works well for anything except games.
I am using some DirectX-heavy designer software for hobby purposes. Also, I have a rather old comp (one of the reasons why i tried Xubuntu as well), so having WINE mimic a Windows environment will probably be demanding enough.

---

### Post by ago on 2008-01-29
> **Baltirow said:**
> Could you please elaborate on that second sentence? I'm still quite the newbie in this field.
I am using some DirectX-heavy designer software for hobby purposes. Also, I have a rather old comp (one of the reasons why i tried Xubuntu as well), so having WINE mimic a Windows environment will probably be demanding enough.

Each operating system uses some bootloader. Each bootloader has normally a mechanism to boot a different operating systems or pass the ball to another bootloader (chainloading).

For instance we have support for Win98 bootloader, Winx XP bootloader, Vista bootloader, and in each case we chainload to grub4dos (wubildr.mbr) but I have little clue how the ME bootloader works. I am sure there is some way to chainload to wubildr.mbr, we just did not receive enough requests help so far to implement it and I have no intention to buy ME... If you can provide enough info/testing I can add it to wubi.  

Wine by the way is not an emulator, it is a set of native linux libraries that mimics the windows API calls. So windows program do find the dll they are used to, that to their eyes behave as the windows counterparts, except that those dlls are native linux libraries, written and compiled for linux. Hence there is (almost) no penalty. Whether or not your apps are supported is a different story.

---

### Post by ago on 2008-01-29
Another option is to install grub4dos as your main bootloader since that can ceirtanly chainload to windows-me bootloader while the reverse is not necessarily true.

---

### Post by WutCake on 2009-06-27
sorry for revival,
but i have this problem, i installed wubi that i got off the ubuntu website, it looks like it finished but it closes suddenly.

when i reboot, my laptops boots up normaly, meaning it boots vista.

i had it working before but i had to uninstall it because of some reason i forgot.
:3

thanks.

---

### Post by WutCake on 2009-06-29
_[SIZE=1][SIZE=4][COLOR=DarkOrange]B[/COLOR][/SIZE][SIZE=3][COLOR=Indigo]u[/COLOR][/SIZE]**[SIZE=2][COLOR=DeepSkyBlue]m[/COLOR][/SIZE][SIZE=1][COLOR=Lime]p[/COLOR][/SIZE]**[/SIZE]_ :guitar:

---

### Post by itsjareds on 2009-06-29
Is Ubuntu a program listed under Add/Remove programs? Also, is there a folder in C:/ubuntu, and is it as large as your Ubuntu virtual disk is?

---

### Post by WutCake on 2009-06-29
> **itsjareds said:**
> Is Ubuntu a program listed under Add/Remove programs?
yeah'
> **itsjareds said:**
> Also, is there a folder in C:/ubuntu,
yeaz'
> **itsjareds said:**
> and is it as large as your Ubuntu virtual disk is?
nope, the folder is 709mb big :shock:

---

### Post by itsjareds on 2009-06-29
> **WutCake said:**
> nope, the folder is 709mb big :shock:

So that is smaller than the amount of space you gave Ubuntu? Sounds like it just messed up while trying to create the filesystem.

---

### Post by WutCake on 2009-06-29
> **itsjareds said:**
> So that is smaller than the amount of space you gave Ubuntu? i gave ubuntu like 5 or 6GB.

> **itsjareds said:**
> Sounds like it just messed up while trying to create the filesystem.

i agree, but i did reinstall wubi like 4 times before i posted.

---

### Post by itsjareds on 2009-06-29
I'm fishing here.. try installing Wubi from Safe Mode with Networking (if you haven't already downloaded the .iso).

---

### Post by WutCake on 2009-07-01
> **itsjareds said:**
> I'm fishing here.. try installing Wubi from Safe Mode with Networking (if you haven't already downloaded the .iso).
i don't see why that shound make any difference, but i'll try.

Edit: no difference.

---

