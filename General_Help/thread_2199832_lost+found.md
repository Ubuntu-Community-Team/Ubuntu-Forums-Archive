---
title: "lost+found"
date: 2014-01-16
forum: General Help
---

### Post by bc.haynes on 2014-01-16
I don't know where to go or what to do. I originally had a Windows machine that (I now know) was infected with rootkits. When I ran a virus scan (McAfee) the word "rootkit" kept coming up in the scan. I googled "rootkit" and found out what it was. I tried to use 'Rootkit Remover" (free from Mcafee), but after 4 uses & 4 scans, there were still 28 instances of "rootkit" in the scan. I downloaded ubuntu 12.04, and I put it on a usb stick. I wiped my Windows disk, and installed ubuntu. I tried to format the usb drive (fat32) and it said I did not have the proper authentication to do so. I then tried formatting with ext4. This uncovered a hidden locked folder named "lost & found." The usb stick was infected, and it was flagged as a "boot" device. I checked all my usb sticks and all were infected. I cannot delete this file or format it. I checked in the ubuntu file system and found a "lost & found" folder and double-clicked on it, and was told that I did not have authorization to open it. Ubuntu is infected. And every time I plug in a usb stick, it gets infected. I can't download another distro, or it will be infected. Will I have to trash my usb sticks and my hard drive? (bummer) Where do I go , or who do I need to tell about this? This infection is so sophisticated that it had McAfee reporting "No In fections."

Thanks for reading this long post.  Ben

---

### Post by efflandt on 2014-01-16
lost+found is common for Unix like file systems. It is not a virus, it is where corrupted files go that cannot be recovered when the file system is checked for errors.

```
efflandt@xps8100-1204:~$ ls -dl /lost*
drwx------ 2 root root 16384 May  9  2013 /lost+found
efflandt@xps8100-1204:~$ uname -a
Linux xps8100-1204 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


efflandt@xps8100-1204:~$ ssh freeshell
$ ls -dl /lost*
drwx-----T  2 root  wheel  2048 Oct 13 00:36 /lost+found/
$ uname -a
NetBSD sdf 6.1_STABLE NetBSD 6.1_STABLE (SDF6.amd64) #0: Tue Nov 26 12:49:14 UTC 2013  root@bjork:/spare/netbsd/src/sys/arch/amd64/compile/SDF6.amd64 amd64

$ ^D
Connection to tty.freeshell.org closed.

efflandt@xps8100-1204:~$ ssh typhoon

Welcome back to XNet Information Systems
Today is: Thu Jan 16 00:46:38 CST 2014
There are 14 users on the system.

typhoon:/home/customer/efflandt% ls -dl /lost*
drwx------   2 root     root         8192 Jul 29  2003 /lost+found
typhoon:/home/customer/efflandt% uname -a
SunOS typhoon 5.9 Generic_112233-11 sun4u sparc SUNW,UltraAX-MP
```Note that it only has permission for root user, so to see if anything is in it in Ubuntu you typically would need to use: **sudo ls -l /lost+found**

---

### Post by deadflowr on 2014-01-16
Don't know about the windows infection but here the meaning of lost and found
[http://askubuntu.com/questions/2115/whats-lostfound-and-where-did-it-come-from](http://askubuntu.com/questions/2115/whats-lostfound-and-where-did-it-come-from)

Added, efflandt gave a nice summation.
I be ninja'd.

---

### Post by seanwilson684 on 2014-01-16
I am suprised if you found it now, could have been a remnant from when you had windows. Rootkits install onto the part of the hard drive which is meant to store info about its model number and the partition table. Since you are using ubuntu you should be fine the rootkit probably was meant to do things to the windows OS not linux. Most of the time rootkits are used to stop antiviruses from being able to see a file or to make the antivirus not work at all, even if you reinstall your antivirus and even sometimes if you reinstall windows. What you can do to fix this is:
1. Install windows on a partition or different hard drive (infected hard drive must still be plugged in)and load hitman pro from here: [http://www.surfright.nl/en/hitmanpro/](http://www.surfright.nl/en/hitmanpro/) , not sure if it works with wine.
2. just ignore it
3.if you used btrfs backup your partition onto a external hard drive and put the image on a new hard drive and destroy the old hard drive (don't distribue infected hard drives, that's rude)

---

### Post by bc.haynes on 2014-01-16
Would a corrupted file "trash can" like lost+found be able to replicate itself and hide and be locked? Could it fool McAfee Rootkit Remover into listing "No rootkits" during a scan? I don't agree that this is a normal lost+found file. I believe it is a rootkit installer disguised as a lost+found folder. When I was using Windows, I had problems with Thunderbird that I could not figure out....I was hacked.

---

### Post by 3rdalbum on 2014-01-16
Sir, with due respect, you have been using Ubuntu for less than 16 days. Quite frankly you would not know what is normal on a Linux system and what is abnormal. I've been using Linux for eight years and I can tell you that the Lost+Found folder is totally normal. I have seen it on every Linux system, even straight after installation on a computer with no Internet connection. Only the root user can open the Lost+Found folder. not an ordinary user account, which is why it appears "locked" to you, and why you can't open it.

Rootkits exist, but they don't spread themselves like viruses (not even to USB drives). Rootkits must be installed as a targeted attack, and there must always be some way for the attacker to get into the computer; usually it's via a web server or FTP server that the victim has installed but not set up properly. You don't have any of that.

You DO NOT have a rootkit on Ubuntu - at least not as far as anyone here can tell. And if you had any rootkits on Windows, they were wiped out with the rest of the hard disk.

I think you may be overly paranoid from your time on Windows. We don't get viruses, and only server admins get rootkits (even then, only very few of them). I'm not saying you should go through life not caring at all about computer security, but on Ubuntu you can afford to relax a bit. By comparison to Windows we are like a vast, unspoilt paradise.

---

### Post by deadflowr on 2014-01-16
> **bc.haynes said:**
> Would a corrupted file "trash can" like lost+found be able to replicate itself and hide and be locked? .

No.
The McAfee scanner you have, surprisingly, is working well.

---

### Post by bc.haynes on 2014-01-16
Thank you, 3rdalbum for easing my mind. I **am** very paranoid about systeem integrity. My machine was cracked and info was stolen a couple of years ago, and I fear it happening again. [still paranoid>] Why would my usb sticks be flagged as "boot" when I had only used 2 (of the 4) to install programs (Ubuntu)? Why is there lengthy hard disk activity when one of the sticks is plugged in? I will pull my usb sticks out of the trash can and try {sudo ls -l /lost+found} and see what I get on each one.  Please pardon any typos, I am vision-impaired and can't type. Thanks again for your reassurance that my system is "normal."        I was on the forums 4-5 years ago and they had a way to give kudo/thank you points to a helper. Are they still doing that?    Ben              I like your group photo and your philosophy.

---

### Post by bc.haynes on 2014-01-16
I tried: {sudo ls -l /dev/sdb1/lost+found } and got a "no such file or directory" . sdb1 is my usb stick port. What am I doing wrong? [I did it fout times before I got the spelling and the syntax right (I think).    Ben    Anyways, something is wrong.

---

### Post by deadflowr on 2014-01-16
> **bc.haynes said:**
> I tried: {sudo ls -l /dev/sdb1/lost+found } and got a "no such file or directory" . sdb1 is my usb stick port. What am I doing wrong? [I did it fout times before I got the spelling and the syntax right (I think).    Ben    Anyways, something is wrong.

/dev/sdb1 is the partition. It needs a mount point first.
you would run
```
sudo mount /dev/sdb1 /mnt
```
which would make the the direcotry /mnt the mount point.
then you'd run the command above but replace the /dev/sdb1 with /mnt.
```
sudo ls -l /mnt/lost+found
``` 
This, of course is a very generic layout, there are options you can add as well, if you want.

```
man mount
```

---

### Post by The Cog on 2014-01-16
/dev/sdb1 is a representation of the raw device bytes. You should not work directly on that. You need to "mount" the device, that is to make the logical contents of the disk appear in you filesystem. This is probably easiest done in the file manager. It's a while since I used nautilus, the Ubuntu file manager, but I think you can turn on a sidebar with a list of devices where you should be able to see sdb1 (or some other name like 2G Disk). Double-clicking that should mount it and open the contents in the file manager.

If you want to do it from command line, it goes something like this:
```
# First make a folder for the contents to appear in...
sudo mkdir /mnt/sdb1

# Then mount the drive into that folder...
sudo mount /dev/sdb1 /mnt/sdb1

# List the contents...
sudo ls -l /mnt/sdb1

# Unmount it again (note the spelling of the command umount)...
sudo umount /mnt/sdb1
```

EDIT:
deadflowr beat me to it. We chose different mount points though. I tend to make folders beneath /mnt so I can mount multiple drives if I want. But that's just habit, really.

---

### Post by silvervulpus on 2014-01-16
ok dude. gotta agree with 3rdalbum here. if you had a rootikit on  windows, it was gone when you removed windows from your partition table.  secondly your usb drives wont get rootkits just from touching a system  that has one. third of all,not all rootkits are viruses. the ubuntu  installer along with many other forms of OS installers that you run from  a flash drive IS a rootkit. not all rootkits are viruses. some rootkits  are necessary for the installation of a new and clean OS such as  ubuntu, puppy, fedora, or even crunchbag. which is why uefi instead of  bios can burn and die for all i care...(stopping root kits my hairy  cheeks more like trying to stop linux boot loaders from making microsoft  hardware into beautiful linux machines, screw bill gates and windows!)  fourth thing, chill on the paranoia... macafee is a total crap program  and not even worth using. if your wasting your time on a windows OS the  best protection you can have, and its free, is to have malware bytes,  spybot search and destroy, and avg free, all of these can be obtained  from majorgeeks.com for free legally. also, if you really think you have  a rootkit virus, try running tdsskiller.exe its a great program  designed just for rootkits and is free. beware, it might try to destroy  your Linux boot loader so read carefully and make sure to research  whatever it finds. do us all a favor and delete mcafee forever and never  again waste money or time on it, and if you do go back to windows  either use 7 or XP prosp3.

---

### Post by bc.haynes on 2014-01-16
Thank you,  Ben

---

### Post by mörgæs on 2014-01-16
Thread title changed.

---

