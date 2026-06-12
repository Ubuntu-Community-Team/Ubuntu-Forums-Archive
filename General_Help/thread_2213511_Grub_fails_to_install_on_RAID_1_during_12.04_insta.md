---
title: "Grub fails to install on RAID 1 during 12.04 install"
date: 2014-03-27
forum: General Help
---

### Post by Tony_Lillie on 2014-03-27
There seems to be a ton of material out there on this subject, but I've been researching most of the day now and can't find the solution.

During installation of 12.04 using software raid configured through the alternate CD, the grub fails to install with a fatal error. Apparently it is trying to install grub to sda which is NOT correct as it should be installing it to md126 which is the proper partition of the RAID 1. (I have no issues partitioning the disks and creating the array.)

I've read several posts that indicate I should be able to change the default grub install location, but I can't figure it out. I see no options or menus of any kind that would allow me to do this. The install just rolls on like a freight train and then hits the error. Eventually I gave up and finished the install without the bootloader.

So, now I have a perfectly good RAID 1 install, but no grub bootloader. I would fix that, but I really want to know how to get the installation right in the first place.

Help please.

---

### Post by Kirboosy on 2014-03-27
You should use Ctrl + Alt + F3 to open up a new TTY. From there you should be able to run the command ```
sudo fdisk -l
```

This will list out the drives attached to your computer. When I recently went through setting up my RAID10 GRUB had problems knowing where to install. So I figured out using fdisk that I needed to install to ```
/dev/mapper/sv_21lkdfjr (I don't remember the exact location but yours will vary most likely)
```

After you determine the correct RAID to install too you can switch back to your original screen with Ctrl + Alt + F7.

Hope that helps!
~Caboose

---

### Post by Tony_Lillie on 2014-03-27
> You should use Ctrl + Alt + F3 to open up a new TTY. From there you should be able to run the command
When should I do that, and what is a TTY? Is that a terminal?

When I reach the Grub Bootloader installation portion of the install process and press Ctrl + Alt + F3 I get a Busybox Shell. When I run the commands you indicate, I get "not found" errors.

There seems to be some kind of disconnect here...

---

### Post by Kirboosy on 2014-03-27
Yes, think of a TTY as just another terminal to run things in. 

You should open up the TTY3 when the installer fails to install GRUB and it asks you the path to install GRUB too. 

Maybe the "not found" portion of the command is the sudo. You might not need sudo. Try running just ```
fdisk -l
```

Hope that helps!
~Caboose

---

### Post by Tony_Lillie on 2014-03-27
I was able to open a shell, which I presume is similar to a terminal, but I could not get the command ```
fdisk -l
```to work either with or without sudo.

I decided to take a closer look at the Advanced Installation Instructions at the following URL [https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)   for a 4th time and discovered I was bypassing an apparently important step. Actually I should rephrase that and say I just missed a step. A tiny seemingly insignificant step contained in these words ```
[COLOR=#333333][FONT=Ubuntu]Select the first hard drive, and agree to [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]*"Create a new empty partition table on this device?"*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu].[/FONT][/COLOR]
``` PLEASE NOTE it says select the HARD DRIVE and not a partition. This is what I was not doing, and was the root of my issue.  
So, today I've learned to read slower and be more anal & methodical than ever before, because EVERY !@#$ step is CRITICAL and nothing can be missed [B]EVER EVER EVER!
[/B]
I'm so pissed at myself right now.... ughhh!

Thanks for trying to help me...when I can't even help myself.

---

