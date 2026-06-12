---
title: "Boot Loader gone - Dual Boot Kubuntu/Windows"
date: 2014-03-10
forum: General Help
---

### Post by Majik_420 on 2014-03-10
So I was trying to fix Windows again... Its been a couple years now since I have been able to boot windows. I try every few months to get in but I just can't get it. I just miss having actual Photoshop instead of GIMP, Only thing I really want windows back for. My student version is installed on this computer and I'm afraid I won't be able to install it anywhere else because of CD keys or whatever.  

And Of course my last attempt at getting into windows, did something to the bootloader. Now it just automatically tries to boot broken windows7 and I have no choice to boot kubuntu.

I tried what little I know, but I just cant get the grub loader back. I'm using Slax on CD right now for internet access but I haven't done anything geeky in a while so I'm a little rusty with digging my way outta this hole.

Any thoughts or suggestions?

---

### Post by phidia on 2014-03-10
Have you tried [boot-repair]("https://help.ubuntu.com/community/Boot-Repair")? there's a how-to at the inserted link.

---

### Post by Majik_420 on 2014-03-10
I'm trying to figure it out. 

My Kubunutu cd wont load the Try me feature, so I did an error check and it says it has one error. I'm guessing that error doesn't go away.

So that means I have Slax and Slacko, and I haven't used terminal in the live cd's much and I can't seem to get anything to work. I downloaded the boot repair while on Slax, but couldn't figure out how to get into it. I put Slacko back in since it seems to have more tools, but I don't see Boot Repair, and I can't get terminal commands to work.

I'll keep trying, but I would love some help. I used to know my way around a little better, but haven't done any computer stuff in a couple years and I feel lost.

*Burning boot-repair to cd, gonna try to boot into that and hopefully that fixes my problem.

**Ok Working in Boot Repair CD now. its telling me that my linux partition sda5 is maxed out on space, which it is, its at like 99%, and that it can prevent starting. I have to figure out how to delete files and then proceed with the boot repair. 
It automatically gave me a browser window to delete or move files from sda5, but I see no way to delete or move in that browser window. I'm thinking I'll have to mount the partition and then I should be able to modify contents through the file explorer?

---

### Post by Majik_420 on 2014-03-10
Just a bump for my most recent update. Any info on getting into my linux partition to free up space? Or I could actually try to shrink my broken windows partition? or just get rid of it altogether? ugh headache.

---

### Post by oldfred on 2014-03-10
Generally best to only use Windows tools on Windows partitions as it always needs chkdsk after a resize.

If you remove files from full partition be sure to empty trash if not deleted immediately. Not sure if from live installer if it will go to trash or not.

Most of this is after you have booted.
       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by Majik_420 on 2014-03-10
Is boot repair for windows? I was thinking it would help me get GRUB back so I can load into Kubuntu...

And If I can get into the partition I just need to delete a few movie files. Mostly just a movie/Internet computer, but I am still not sure about getting into those files.

*Copy/pasted address from browser and put into file explorer, opened as root, and then I could right click, shift+delete the files to free space. I only deleted a handful of movies and it told me my partition was still full, but continued anyway.

Worked through the prompts and terminal commands and looks like a reinstall of GRUB and tells me now I can reboot.

I'm just gonna leave this here,
"Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/7070495/](http://paste.ubuntu.com/7070495/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer."

Fingers Crossed.

---

### Post by Majik_420 on 2014-03-10
Boot Repair fixed the GRUB, im back on my kubuntu.
Now I just need to figure out what to do with my broken windows.

---

### Post by oldfred on 2014-03-10
Your Windows boot files all look like they are there. It just may need a chkdsk from a Windows repair CD or flash drive.

You also may want to houseclean old kernels.

       Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

---

### Post by Majik_420 on 2014-03-10
I was just about to ask if about I continue working on that problem if there are any commands or procedures I should avoid to keep everything else working smoothly.... for example I think what screwed me over this time was I was trying to fix windows booting, and I think I did a fixmbr command or something and I think thats what messed up GRUB, and Windows still wouldnt boot anyway.

And in response oldfred, I am really confused on the windows side right now. The issue there is that the windows logo does not appear at boot screen and nothing happens, just says "windows loading" or whatever indefintely. I ran the startup repair program but it cant complete and I was discouraged by some words used in that report. Something about problem signature 05 autofailover and problem singature 07 noosinstalled. I also got a different one that said something about baddisk. I know thats kinda vague, i have to get back into that problem.

I don't have a repair cd, I have a cd, that is basically the same thing I can get on the computer, just the same windows trouble shooting programs that I can't make any progress with.

I cleared out 3 old kernals.

---

### Post by oldfred on 2014-03-11
Grub can really only boot working Windows. And sometimes you do have to run the fixMBR to temporarily put a Windows boot loader back in to directly boot to get to f8 and do other repairs. 
Always best to have a repairCD or flash drive for the current version of every operating system you have installed. Ubuntu live installer works, but I usually have Boot-Repair, Supergrub, gparted's live version and maybe others.
I did make a Windows 7 live repair flash drive back when it was a free download, but now it costs.
If you have access to another Windows 7 system, it just needs to be the same 32 or 64 bit and then any version.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

