---
title: "Permissions and networking and Kodi, oh my!"
date: 2017-06-01
forum: General Help
---

### Post by JP_Rockagetty_III on 2017-06-01
Hello,

I'm sorry I must ask for help in this forum, but I must.  When I try to read the wiki and how-tos and such, I am overwhelmed with information my brain 'locks up'.  Also, I am close to success with my Ubuntu machine.  Here is my system:

Asrock AM1H-ITX mini-ITX board
AMD CPU, 8 GB RAM
fanless CPU cooler
Seasonic fanless PSU (460W or 520W, I forgot which)
generic mouse, Unicomp "clicking" keyboard (just like IBM Model M)
(this motherboard has an "extra" SATA controller in addition to the one on the CPU, so I can have 4 SATA drives)
Sending video from the CPU/GPU out the HDMI port to my 39.4" flat-screen Toshiba TV.

I am running Ubuntu 14.04.1 64-bit (kernel 4.4.0-31-generic #50)
I am running XBMC Debian Package version:2:12.3+dsfg1-3ubuntu1

SATA drive #1 is a 480 GB Samsung EVO 850.  It consists of:
18 Gigs for / (only 4.3 GB used)
then swap
then 424 GB of ext4 space for /home (only 39 GB used - photos, spreadsheets)

SATA drive #2 and #3 are 3 TB spinners, they are in an LVM2 configuration (so Ubuntu thinks it is one giant 6 TB drive).  This is where my Kodi stuff is (TV programs I recorded off the air with the HDHomeRun Dual, MP3s and other stuff).

I would like to do two things:

First, I want to share the 424 GB of space on /dev/sda6, giving everybody read, write and execute permissions.  Right now, /dev/sda6 is mounted on /home.  The share "/home/Shared Documents" is chown mike, chgrp mike, and that directory is drwxrwxrwx.  Below that, all subdirectories and files are "chown nobody" and "chgrp nogroup".  Subdirectories are rwxr-xr-x and files are rwxr--r--.  The 39 GB of files seem to be accessible from the local Ubuntu machine and from my Win7 machine (drive letter X), so things really seem good here.  Should I have put this share under "/home/mike" instead of "/home/Shared Documents"?  Would things have been simpler that way?

Second, I would like to share the 6 TB of LVM2 space (secretly two 3 TB spinners), so other computers can run Kodi and play audio/video files from across the network (I recently upgraded hardware to 10/100/1000 and wireless "N").  I have about 900 GB of files.  I believe I created the share from the GUI.  Here is the output from the "mount" command:

/dev/mapper/mikes--movie--disks-mikes--movies on /media/mike/90ecabe1-aeed-41ca-a3fd-471cb60e11fc type btrfs (rw,nosuid,nodev,uhelper=udisks2)

The directory /media/mike/90ecabe1[snipped] is "chown nobody", "chgrp nogroup" and drwxrwxrwx.  Directories below that ("My MP3s" or "Recorded TV") are "nobody" and "nogroup", and drwxr-xr-x.  The actual media files are "nobody", "nogroup" and rwxr--r--.

Kodi (on the Ubuntu machine) won't play MP3s or recorded media.  Is it because the directory /media/mike/90ecabe1[snipped] is "chown nobody" and "chgrp nogroup"?  I don't dare issue "chgrp mike" and "chown mike" for that directory by force, since that is determined in /etc/fstab.  And I don't think I should modify anything in /etc/fstab (maybe years ago under Mandriva you could edit to turn on read-write for NTFS, if you knew it would work).  Note that my Win7 machine is playing an MP3 from the 6TB LVM (drive letter Y) as I type these words with no problem.

Is my 6.0 TB LVM drive mounted in an awkward way/location?  What directories should my media files be located at?  Is sharing an LVM2 pair of drives (with my MP3/video files) any more difficult than an ordinary share?

I know Windows 7 (and Kodi for Windows) can manage and serve the files like I want ("dynamic disks" instead of LVM), and sharing directories/partitions is a few mouse-clicks away.  I'm trying to give Linux the benefit of the doubt.  But it is hard.  Can someone help me?

---

### Post by TheFu on 2017-06-01
I'm not good at *word problems*.
Please post, using **code tags**, the output from 
* df -h
* lsblk
* ls -l (for each directory/files you want to share)
* List of all the client OSes involved.

Have you considered using a real media server, not just a player?  That would make all the sharing for playback much easier.  Wouldn't it be handy to have Android clients access all the media easily or access all of it from outside the LAN using a VPN or SOCKS proxy?  File sharing doesn't really work well for that stuff.

Just to be clear, I like kodi for playback, but find it lacking as a "server" to other systems. Plus lots of people report issues using samba to share media. 

I hope you have backups.  Lost 80% of my data spanning disks using LVM. 1 disk failed. Lost all the data on it and all the others.  Just sayin'.

---

### Post by JP_Rockagetty_III on 2017-06-01
I have tried fussing around with the shares before, let me try re-setting them one more time.  The data on the LVM (TV shows, can be replaced) should still be intact.

Basically, I want to use most of my boot drive (SSD) for docs, spreadsheets, pictures, etc. and the two LVM2/JBOD/whatever spinners will be for ripped TV shows.  No passwords, all access everywhere (for simplicity).  Sounds easy, right?

(I could not do this with most of these ITX boards, since they can only handle 2 drives.  But this one lets me have four - one boot drive, two for LVM, and one spare.)

I don't really watch TV on my Galaxy S5, and I don't know a single thing about VPN or SOCKS, sorry.  I only know one thing about my home network - when using photo manager software, it takes a long time to load thumbnails or full pictures - data has to come from the SSD inside a USB enclosure plugged into the Netgear WRT-AC1200.  I live with this delay.

> I hope you have backups.

The LVM2 data can be replaced.  But I do feel your pain.  In autumn of 2015 I plugged the wrong power plug (pinouts on modular PSUs/cables are NOT all the same, even though the plugs may fit!) into my 1.5 TB drive and fried a chip on it.  Kroll Ontrack got practically everything back (tax docs, e-mail, executables), but it cost $1400.

Let me try fussing with the shares one more time.

BTW, if you believe Kodi will be a bad choice for server, what do you recommend?

---

