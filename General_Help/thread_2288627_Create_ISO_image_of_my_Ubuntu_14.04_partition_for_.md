---
title: "Create ISO image of my Ubuntu 14.04 partition for use with a bootable USB stick"
date: 2015-07-28
forum: General Help
---

### Post by MagisterDixit on 2015-07-28
I know how to create a bootable USB stick on Ubuntu using a downloaded ISO file ([http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)). I want to create my own ISO file of my Ubuntu so that I don't have to re-do all my costumizations and apps every time I put Ubuntu on a new computer. I have searched for an easy way to do this and come up empty. I can't figure out how to get remastersys on my computer and dd and clonezilla are making my head hurt. Is there a simple way to create the image I want? How?? If it is not painfully obvious by now, I am a novice so please use small words and speak slowly. Thanks!!!!

---

### Post by oldfred on 2015-07-28
I do not know answer to your question as I do it differently. There have been other posts with your same question, but usually I do not comment.

Almost all your settings are in /home as is your data if you have not configured separate data partition(s).
And as soon as you use system after making the image copy, it is outdated. How often will you really recreate it?

But my backup procedure is just to be able to reinstall and reconfigure my system. And since I may use for a new install also, I now have some scripts to automate some parts of a reinstall.

You should be backing up anyway, and I see no reason to backup all of Ubuntu as that is easy to download and reinstall. As long as you have high speed Internet the updates are quick & easy.
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by sudodus on 2015-07-29
What you want is a rather advanced task, and you cannot expect, that it will be very easy.

However, Clonezilla is not that difficult. After trying and testing a couple of times, I think you can manage it, at least if you stick to beginner mode. I think it is harder to make Remastersys and similar tools to work. Then you are getting close to making your own linux distro, or at least a re-spin.

Another option, that works if you have a simple system with 'only' a root partition and a swap partition is to use the One Button Installer: create a tarball of your system, and install it easily into other computers with the One Button Installer. If you intend to follow this path, I can help you.

-o-

But re-read oldfred's post and its links. It might be enough with a backup of your installed system, or only your personal files and tweaks.

---

### Post by tea for one on 2015-07-29
> **MagisterDixit said:**
> I know how to create a bootable USB stick on Ubuntu using a downloaded ISO file ([http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)). I want to create my own ISO file of my Ubuntu so that I don't have to re-do all my costumizations and apps every time I put Ubuntu on a new computer. I have searched for an easy way to do this and come up empty. I can't figure out how to get remastersys on my computer and dd and clonezilla are making my head hurt. Is there a simple way to create the image I want? How?? If it is not painfully obvious by now, I am a novice so please use small words and speak slowly. Thanks!!!!

Good morning

You may want to have a look at Systemback.

More information can be found on the launchpad page:-

[https://launchpad.net/systemback](https://launchpad.net/systemback)

---

### Post by leunam12 on 2015-07-29
When I built the computer that I use now I just took the HDD from the old computer and put it in this one and ran boot-repair (only because I wasn't dual booting before and now I am). Everything started normally and I have never had a problem with it. If that worked, I imagine that cloning the disk and installing on another computer should work the same.

---

