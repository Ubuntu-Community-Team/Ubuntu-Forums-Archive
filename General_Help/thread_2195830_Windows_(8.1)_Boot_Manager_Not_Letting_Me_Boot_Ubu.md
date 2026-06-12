---
title: "Windows (8.1) Boot Manager Not Letting Me Boot Ubuntu 12.04"
date: 2013-12-26
forum: General Help
---

### Post by inthefold on 2013-12-26
I just did a side-by-side install of Ubuntu 12.04 on my Windows 8.1  machine. Both OS work fine. However, when I start the machine, instead  of getting a grub menu, I get a Windows boot manager menu which does not  allow me to boot Ubuntu. When I choose the Ubuntu option, it takes me  to a screen which says something to the effect of "Windows is not  loading". Well, I'm not trying to load windows, I'm trying to load  Ubuntu. In order to actually boot Ubuntu, I have to go through the BIOS  option in the windows boot manager which involves about 6 steps and is a  real pain as opposed to the one or two steps I've seen on others'  machines. Should I remove windows boot manager? How would I go about  this? Maybe grub is not installed, but I don't know how to check this.  Is it ok to have grub and windows boot manager or should I just stick  with grub? I've used ubuntu before but am a total noob to dual-boot.  I've tried pressing esc and several different function keys while  restarting to no avail. On my old machine, I just wiped windows and used  ubuntu exclusively but I need windows for Rosetta Stone which installs  and opens but does not function on Ubuntu. Tried [COLOR=#000000]EasyBCD [/COLOR]but it only got me to the point where I am now. Any help making my boot options easier would be greatly apprectiated.

---

### Post by RookY2K on 2013-12-26
I had pretty much the same problem when I installed Ubuntu 13.10.  I used this utility and it solved the problem: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair).

---

### Post by inthefold on 2013-12-26
@ RookY2K Just tried that utility and incurred folllowing error: 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [1,095 B]
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [3,119 B]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [3,119 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Fetched 19.2 kB in 11s (1,607 B/s)
W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

Obviously, I was not able to install and thus, the problem was not fixed.

---

### Post by oldfred on 2013-12-26
Did you install the 32 bit version not the 64 bit version? Only the 64 bit version has UEFI support and can be dual booted with Windows 8 in UEFI mode.

The 32 bit version would be BIOS boot only and then you do have to turn off secure boot, UEFI  boot and turn on CSM/Legacy/BIOS boot mode only for it to work.

Post one or several of these. If x86_64 then you do have 64 bit.
       cat /etc/*release
cat /etc/lsb-release

 uname -a

---

### Post by inthefold on 2013-12-27
Yes I did install the 64 bit.....The grub actually does show up. However, it is only after I've taken the 6 or so steps to launch Ubuntu. By that time the grub does me no good

---

### Post by oldfred on 2013-12-27
Have you tried 13.10? 
Very new computers have the newest chips & hardware. Intel offered many updates to kernel & video drivers that are now in 13.10. They should be in 12.04.4 in Jan, but now 12.04.3 is not as up to date.

---

### Post by inthefold on 2013-12-27
I went with 12.04 because it's a LTS verison. So, is LTS not as important as I thought?

---

### Post by oldfred on 2013-12-27
Many like the LTS and I am running the 12.04LTS, but will upgrade when 14.04LTS comes out in April. My wife complained about changes as I had upgraded every 6 months since 6.06. :) And back then my dual core system was new hardware and I had a lot of issues. Now very few. But I have lots of room on one drive, so I have 14.04 running already and for me it mostly works. I also have 13.10, 13.04 & 12.10 in 25GB / (root) partitions just to see the changes and if they still work well with my system.

But the very new hardware and new UEFI are going thru a lot of changes. And the newest Linux then works better. Many features have to be reverse engineered as the vendors normally do not provide much support. So it takes 6 mo or a year before Linux usually works well with very new hardware. Intel has been good about offering kernel fixes and new video driver updates for its open source (only) video driver. But again it takes a while before distributions roll those changes out in a complete distribution.

---

### Post by inthefold on 2013-12-27
So the intel will have a fix in Jan? Would I just dl it from intel's site? Maybe I will try 13.10 instead. I just don't really do a lot of heavy computing and would feel better about having something that will be supported long-term. Are there any other possible fixes for this issue? Could I remove windows boot loader? Or maybe install grub in windows? I appreciate the help.

---

### Post by oldfred on 2013-12-27
You should be able to upgrade from 13.10 to 14.04. 
It just is that I did upgrades from 6.06 thru 9.04 every 6 months and had some issues with upgrade. Required effort to make it work each time. I then did a clean install of 9.10 as I was converting from 32 bit to 64 bit and that just worked. So I now prefer just to do another clean install into another 25GB / (root) partition and keep data separate to make a clean install easier.
Some post upgrades work and others have issues. Depends on how much customization you have done as often best to undo ppa's and some other proprietary drivers before an upgrade.  And it seems to just depend on luck of the draw on what hardware you have. Sometimes new install works where old required lots of customization to make it work. And occasionally the other way around.

---

### Post by inthefold on 2013-12-27
Installed 12.04 via USB (side-by-side windows 8.1) on my new HP 2000 Windows 8 laptop after upgrading to Windows 8.1. Had issues with windows boot loader and grub so I spent yesterday trying to make my Ubuntu boot smoothly. I am somewhat of a noob (total noob when in comes to dual-boot), so I bumbled around and seem to have screwed things up......This is the point I'm at now:

when I turn on my machine, it takes me immediately to grub rescue. I am able to boot Ubuntu by using the following command sequence:

root=(hd0,gpt7)
prefix=(hd0,gpt7)/boot/grub
insmod normal
normal

That takes me to the Grub screen. Once at the grub screen, all I can do is boot ubuntu. When I try to boot windows, I get the following message:

error: unknown command "drivemap".
error: invalid EFI file path.

I tried fixing grub in the terminal using the following commands:

sudo update-grub
sudo grub-install /dev/sda

The update installs but does not solve the problem. Also, every time I boot my machine, I have to go through the whole grub rescue insmod mess to get to grub and launch Ubuntu. I need help getting Windows to work as well as not having to go through grub rescue every time I use my computer. Assisstance is greatly appreciated. Thanks!

UPDATE: Tried Boot-repair disc using reccommended settings to no avail

---

### Post by inthefold on 2013-12-27
Hey oldfred, thanks for the advice. I've got some deeper issues now lol. If you've got the time and mind to do so, please check out my other thread and let me know what you think. Thanks a bunch! [http://ubuntuforums.org/showthread.php?t=2196080&p=12884545#post12884545](http://ubuntuforums.org/showthread.php?t=2196080&p=12884545#post12884545)

---

### Post by Bucky Ball on 2013-12-27
***Threads merged.***

Your threads have been merged. While not an exact duplicate it is an extension of this issue where you are getting plenty of help already.

---

### Post by inthefold on 2013-12-27
Ok thanks. Just thought it didn't exactly fit in the absolute beginners section.

---

### Post by inthefold on 2013-12-27
@Bucky Ball.....any advice on this issue?

---

### Post by Bucky Ball on 2013-12-27
Yes, install 13.10 as advised. This thread was never resolved/solved, and the next problem you have posted, which has been merged with this thread, is basically a variation on a theme and a continuation of this issue as a result of what you have tried of the advice here. 

The last advice you were given here was to install 13.10 and see if that works with newer hardware. From what I can see that has been ignored. Try that and report back.

---

### Post by inthefold on 2013-12-28
Was attempting to upgrade but got stuck when I had to restart. Booted back directly to grub rescue and attempted the 
previous process of running normal.mod to get to the grub screen. However none of my .mod files were in the same place. 
I had to dig around and finally found them buried in (hd0,gpt7)/usr/lib/grub/x86_64-efi/ with normal.mod at the top of the list. I typed the following: insmod (hd0,gpt7)/usr/lib/grub/x86_64-efi/normal.mod and got the following message: error: symbol not found: 'grub_disk_dev_list'. Now I'm completely stuck and having to access the forum via smartphone. Need help! Lol. Thanks guys!

---

### Post by Bucky Ball on 2013-12-28
Upgrade or clean install? There's a difference, but as you couldn't get to a desktop or install in the first place, I'll assume you booted from a disk and attempted to install Ubuntu 13.10 (and yes, as oldfred mentioned, you can go directly from that to 14.04 LTS, supported for the next five years ... or you can go directly from LTS to LTS, 12.04 to 14.04 directly, leap frogging the interim releases in between, so six of one, half a dozen of the other, but it appears the 12.04 install was a disaster so 13.10, nothing lost).

From a disk you are trying to install 13.10???

---

### Post by inthefold on 2013-12-28
It was an upgrade. I was able to access my desktop before the attempted upgrade. I'm assuming that I would have to use a separate machine to create a disk. However, how do I get my laptop to boot from a disk or USB when all it does is go into grub rescue when I turn it on?

---

### Post by Bucky Ball on 2013-12-28
You hit whatever key is necessary when you boot the machine to get to your BIOS and change the boot order to boot from optical drive or USB. F12 sometimes works to get to a boot device screen, depends on the machine. To get to the BIOS you could try hitting delete, backspace, F1, F2, but if you have a manual that should tell you the correct key. Pretty much straight after you turn the machine on.

So, just for clarity and apologies, you were upgrading from what to what? 12.04 LTS to 12.10, as that is the only upgrade route from there?

---

### Post by oldfred on 2013-12-28
Also be careful with a new install. Many users end up with Windows having hibernation on, and then from installer it only shows Ubuntu as reinstall choice. But since it cannot see Windows it overwrites entire drive.
Only use Something Else or manual install and be sure to choose existing / as root and it should find existing swap automatically. If you have a separate /home choose that but DO NOT tick the format or it will ease the existing data in /home.

---

