---
title: "Problem after installing with Wubi"
date: 2008-06-12
forum: General Help
---

### Post by BrianZachary on 2008-06-12
[COLOR=blue]I installed Ubuntu with Wubi 8.04 and everything went fine.  At the end of installation, it asked me to reboot to finish the installation, so I did that.  When my computer starts back up, it goes through the normal stuff, then I have the option to choose either Windows XP or Ubuntu.  When I choose Ubuntu, this is what appears on the screen:[/COLOR]
 
 
GRUB4DOS 0.4.3 2008-4-23, Memory: 638K / 702M, CodeEnd: 0x412E0
[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename. ]
 
grub> 
 
 
[COLOR=blue]A blinking cursor sits after the grub>.  When I hit the Tab key, this comes up:[/COLOR]
 
 
Possible commands are: background blocklist boot cat cdrom chainloader clear cmp color commandline configfile debug default displaymem embed errnum errorcheck fallback find foreground fstest geometry halt help hiddenflag hide initrd install is64bit kernel lock makeactive map md5crypt module modulenounzip outline pager partnew parttype password pause pxe quit read reboot root rootnoverify savedefault serial setkey setup setvbe splashimage terminal terminfo testload testvbe unhide vbeprobe write
 
 
[COLOR=blue]I don't know what all this is or what it's for.  All I wanted was to install Ubuntu and go.  I have tried uninstalling and reinstalling with the same results both times.  [/COLOR][COLOR=#0000ff]I have Windows XP Home SP2.  The computer is only a couple years old, so I don't know what the problem could be.[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=#0000ff]If anyone can help me, I'd appreciate it.  If you need any other info, let me know.[/COLOR]
[COLOR=#0000ff][/COLOR]

---

### Post by ago on 2008-06-12
uninstall, if you have wubildr* or grldr* or menu.lst in C:\ or D:\ remove them and install again

---

### Post by BrianZachary on 2008-06-12
> **ago said:**
> uninstall, if you have wubildr* or grldr* or menu.lst in C:\ or D:\ remove them and install again
 
I just looked in my C folder and there is "wubildr" and "wubildr.mbr".  So I should delete both of those?

---

### Post by BrianZachary on 2008-06-13
[COLOR=blue]Ok, that didn't work, ago.  I deleted both of those files in the C Drive, uninstalled Wubi and reinstalled.  When the installation finished, both of those files appeared back in the C Drive.  I rebooted and the same "grub" screen was there.[/COLOR]
[COLOR=blue][/COLOR] 
[COLOR=blue]I did a little experimenting by moving each file seperately to the desktop to see what would happen.  Moving the "wubildr" file didn't change anything, but moving the "wubildr.mbr" made a different screen show up.  When I selected Ubuntu in the selection screen, this message came up:[/COLOR]
 
 
Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.
 
 
[COLOR=blue]So any other ideas would be appreciated.[/COLOR]

---

### Post by ago on 2008-06-13
Try [http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev502.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev502.exe)
It requires a new ISO though the daily desktop CD 8.04.1 (let wubi get the correct one for you).

---

### Post by BrianZachary on 2008-06-13
I tried that one and the same results, I get that "grub" screen.

---

### Post by BrianZachary on 2008-06-13
I don't know if it makes a difference, which is why I didn't mention it before, but I have an external hard drive plugged into my computer through USB.  I have wubi.exe on the external and that's where I've been installing from.  Should I try moving the wubi.exe to my main hard drive and try installing it from that drive, or would this make any difference?

---

### Post by tinybit on 2008-06-14
USB BIOSes could alter drive numbers. Also it is possible that some buggy USB BIOSes might make some real drives hidden or invisible. So you should try to unplug the external drive and reinstall. And at boot time, keep unplugging it.

If there are still problems, run these commands at the grub prompt:

```

debug on
geometry (hd0)
geometry (hd1)
geometry (hd2)
geometry (hd3)
geometry (fd0)
find +1

find --set-root /menu.lst
configfile /menu.lst

```

Post the messages displayed. Note: .lst is for LIST, not for FIRST.

You may also try to copy wubildr and menu.lst into the root dir of your external drive, and see if it will do.

---

### Post by BrianZachary on 2008-06-14
Ok, tinybit.  I will try your suggestion and let you know later what happens.
 
If there are still problems and I'm typing all those into the grub prompt, I don't know what all that is for, but I will try it.  I know absolutely nothing about this kind of thing.
 
As far as copying wubildr or menu.1st into the root dir of my external drive, you have lost me completely.
 
I will move wubi.exe to my main hard drive and try installing from there with my external unplugged first and see what happens.

---

### Post by BrianZachary on 2008-06-14
[COLOR=blue]Well, that did nothing different.  I moved wubi.exe to my main hard drive, unplugged the external, and tried installing wubi once again, but the same result happened...that damn "grub" screen.[/COLOR]
[COLOR=blue][/COLOR] 
[COLOR=blue]I did what you suggested, tinybit, but nothing changed.  Entering "debug on" at the grub prompt did nothing, just brought a new grub prompt onto the screen.  Entering "geometry (hd0)" did this:[/COLOR]
 
drive 0x80(LBA): C/H/S=16383/255/63, Sector Count/Size=263192895/512
Partition num: 0, Filesystem type is ntfs, partition type 0x7
Partition num: 1, Filesystem type is fat, partition type 0xb
 
[COLOR=blue]Entering "geometry (fd0)" did this:[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=black]int13/41(0),version=0, int13/08(0),version=60, C/H/S=16383/255/63, int13/02(0), err=1, biodisk read first sector of drive 0x0: failure! errnum=0 drive 0x0(CHS): C/H/S=16383/255/63, Sector Count/Size=263192895/512[/COLOR]
 
[COLOR=blue]Entering any of the others ended with "[/COLOR][COLOR=black]Error 21: Selected disk does not exist[/COLOR][COLOR=blue]".[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=#0000ff]Like I said, I know absolutely nothing about any of this stuff or how to fix it, so I'm relying on anyone here who can help.  I feel like maybe it's my computer since everything I try ends with the same result and maybe I should just give up trying, at least until I get a new computer, which won't be for a long time.[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=#0000ff]If there are any other things I can try, please let me know because I am running out of patience with this thing.[/COLOR]

---

### Post by tinybit on 2008-06-15
The geometry (hd0) shows you have 2 partitions:
Partition num: 0, Filesystem type is ntfs, partition type 0x7
Partition num: 1, Filesystem type is fat, partition type 0xb

Can you copy the two files, wubildr and menu.lst, into the root dir of BOTH your partitions? You should switch to a newer build for wubi.exe(e.g., the one mentioned above by Ago), in case you are still using a very old one.

If you would like to help the trouble shooting, you may continue the test and post the result of these commands(at the grub prompt):

```

find --set-root /menu.lst
configfile /menu.lst

```

If you just want a quick solution and do not want to test any more, I recommend you re-partition/re-format your drive. Remember to use FAT32 instead of NTFS for your Windows system partition, it can be allocated 20GB or so. You still need one or more large NTFS partitions for ubuntu, so place them after the FAT32 Windows system partition. Next, re-install your Windows and ubuntu. <---- Why this way? Because I suspect GRUB4DOS might have an unknown bug on the NTFS file system type.

Thank you very much for your detailed reports. I know it is a hard work.

---

### Post by BrianZachary on 2008-06-15
> **tinybit said:**
> Can you copy the two files, wubildr and menu.lst, into the root dir of BOTH your partitions? You should switch to a newer build for wubi.exe(e.g., the one mentioned above by Ago), in case you are still using a very old one.
 
If I look in my C Drive, there is wublidr and wubildr.mbr, but I don't see any menu.lst.  I don't know what a "root dir" is or where it is located.  Like I said, I don't know anything about this stuff.  I have tried both the latest wubi.exe from the main site and the one provided by Ago and both had the same results.
 
As for partitions, my D Drive is the only partition other than my main C Drive and the D Drive is the Recovery Partition, so I don't mess with anything in there.
 
> **tinybit said:**
> If you would like to help the trouble shooting, you may continue the test and post the result of these commands(at the grub prompt):
 
```

find --set-root /menu.lst
configfile /menu.lst

```
 

 
It wasn't my intention to "test" this stuff.  I just wanted to install Ubuntu and check it out.  I can enter those commands, but I don't know what I'm doing with that stuff.  I'm not a programmer, so all of that means nothing to me and I don't know what I'm supposed to do with the results.
 
> **tinybit said:**
> If you just want a quick solution and do not want to test any more, I recommend you re-partition/re-format your drive. Remember to use FAT32 instead of NTFS for your Windows system partition, it can be allocated 20GB or so. You still need one or more large NTFS partitions for ubuntu, so place them after the FAT32 Windows system partition. Next, re-install your Windows and ubuntu. <---- Why this way? Because I suspect GRUB4DOS might have an unknown bug on the NTFS file system type.
 
I just re-installed Windows recently and I finally have everything back to the way I want it and I am not going through all that again, so that is not an option at this point.  This is also why I am trying to install Ubuntu through Wubi instead of from a CD or any other way.  With Wubi, the OS can be easily uninstalled if something isn't working right, like with this current situation, but that option isn't available as far as I know with any other installation method.  If I can't get this to work with Wubi, I just won't worry about it until I can get a new computer a few years from now.
 
When someone talks to me about creating, editing or doing anything with partitions or file systems or the like, it gives me a headache because that stuff is very confusing.  I'm not an idiot, but that stuff is not the easiest to understand.
 
> **tinybit said:**
> Thank you very much for your detailed reports. I know it is a hard work.
 
You're welcome.  It's not hard, just a matter of writing down what I see on the screen and posting it in here.  I really hope you don't think I'm being condescending or whatever in my posts, because that's not how I'm trying to sound.  I really do appreciate any help I get and I will try any suggestions short of reinstalling my Windows.

---

### Post by tinybit on 2008-06-15
Try once more(and the last time). Use your Windows explorer to search the whole drive for menu.lst and copy it to the root folder of your C: , then reboot and select ubuntu.

---

### Post by BrianZachary on 2008-06-16
> **tinybit said:**
> Try once more(and the last time). Use your Windows explorer to search the whole drive for menu.lst and copy it to the root folder of your C: , then reboot and select ubuntu.
 
If by "root directory" or "root folder" you mean the C Drive folder itself, that is moot with wubildr and wubildr.mbr since that is where those 2 files are when wubi is finished installing Ubuntu.
 
I did a search for menu.lst and there are 2 of them. One is in C:\ubuntu\winboot along with another wubildr and wubildr.mbr. The other one is in C:\ubuntu\install\boot\grub but that one is the only file in there. So, which one do I copy to the C Drive folder?
 
~~~~~~~~~~~~~~~~~~~~~~~~~~
 
Update:
 
Ok, I tried copying the menu.lst files one at a time and pasting in the C Drive folder and rebooting.  Both times resulted no change...the grub screen still came up.
 
So I am done with all of this for right now.  I'm not a patient person anyway and I've lost any I had trying to get this to work.  It is probably something to do with this computer.  The computer is about 3 years old, but it's up to date as far as updates and programs are concerned.  And like I said, I just reinstalled Windows XP less than a month ago, so I don't know what the problem could be.
 
I just wanted to try something different, but I will just stick to using Windows XP for now.  It may not be as secure or free as Ubuntu, but it works on the computer and I'm more familiar with it.
 
If anyone still has any other suggestions on trying to get this to work, feel free to suggest them.  I just won't be trying them out right now.  One day I may be bored (highly unlikely) and try this again.  Maybe after the next version of Ubuntu and Wubi come out and hopefully this issue I'm having will be corrected.
 
Thank you to ago and tinybit for your help and to anyone else who suggests anything further.
 
Later.

---

### Post by gr3y5t0ne on 2009-01-03
I have the exact same problem, I too have a C: drive and a D: drive, could it possibly be a problem with having 2 drives? I also tried installing Ubuntu 8.10 on my hard drive, but had no success...

---

### Post by creek23 on 2009-01-03
What exactly have you done?

---

