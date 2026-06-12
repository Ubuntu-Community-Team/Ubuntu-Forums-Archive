---
title: "Problems installing"
date: 2014-01-13
forum: General Help
---

### Post by iRbeastware on 2014-01-13
I am trying to install ubuntu 13.10 and 12.04, (any of them for 3 days already). It starts to get on my nerves and I am more than mad with all the issues I am encountering right now.

I get all sort of errors all sort of question mark type boxes with access denied sign. Errors when I try to boot it up, errors when I try to install it, errors after errors after errors and on top of that sometimes when I try to delete a partition or set the partition as I wish to the selected partitions menu it does not even remove or at least open up.

There is something completely wrong with this. I am sick of it.

I have 2 versions of ubuntu!!!

 Everytime I am attepmting an install I completely format the HDDs.

This is wrong !!!!


Here's the steps I follow 

1) Format the hdd completely

2) Open bios

3)Boot from DVD

5)I can't choose Erase disk and so on and so forth from first install option because I get some sort of error with dev/sda and at this point my installer is already blocked I can't access any command, can't close the window cant do s**t, hence I reboot.

6) I choose "Something Else" option and select my partitions.

I put 200 GBs on Ext 4 journaling system, "on /" 

Then put 40GBs on swap area

7) select the 200GBs volume area, and proceed with installing.

8) restart the computer

9) Face this annoying white blinking cursor every single time, for 3 days already.

Please... I am sick of it, I just want to reinstall ubuntu (I dont know how I managed in the first place to install it) and get over with it already.

** Note: I am currently on "Try ubuntu option"**

**I have searched on forums and people say it's a grub error?? hence I tried this:

but,it seems again that there is absolutely no result... 

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# /sbin/grub-install --recheck --no-floppy/dev/sda
bash: /sbin/grub-install: No such file or directory
root@ubuntu:/home/ubuntu# sudo su -
root@ubuntu:~# /sbin/grub-install --recheck --no-floppy/dev/sda
-su: /sbin/grub-install: No such file or directory
root@ubuntu:~# /sbin/grub-install --recheck --no-floppy/dev/hda
-su: /sbin/grub-install: No such file or directory
root@ubuntu:~# sudo su
root@ubuntu:~# /sbin/grub-install
bash: /sbin/grub-install: No such file or directory
root@ubuntu:~# sh /sbin/grub-install
sh: 0: Can't open /sbin/grub-install
root@ubuntu:~# ls
root@ubuntu:~# ls

Please some1 help me... I have run out of patience. It's day 3 already. Some people give up after 2 hours only.



:( :( :( :( :( :(

---

### Post by iRbeastware on 2014-01-13
can some1 help me?? I would greatly appreciate...

---

### Post by mörgæs on 2014-01-13
Please stop bumping your thread.

---

### Post by The Cog on 2014-01-13
It's /usr/sbin/grub-install, not just /sbin/grub-install.

> I get some sort of error with dev/sda This could be important - can you say what the error is?

> annoying white blinking cursor I wonder if this is just the GUI failing to start. If you press Ctrl-Alt-F1, does that take you to a console screen with a working prompt?

---

### Post by iRbeastware on 2014-01-13
I tried ctrl alt f1 and no response.. the only response I get it's from ctrl alt + del... and the system reboots.

I can't remember what it was saying about dev/sda when I tried the first option from install... 

Oh my God I am so upset... I just feel depressed. I am disappointed in many ways. I am currently running a boot-repair app posted on forums ([http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)) , which also doesn't seem to load. It's been 20 minutes since I am running it. It says : Scanning system (os prober) this may take several minutes... counting up to 22 minutes now.

I am depressed :( :( :( :( ... it's been too long guys... 3 days since I am struggling with this. I need to fix it

---

### Post by Impavidus on 2014-01-13
A few simple checks that might help:
- Check the integity of your dvd: [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck). It's a bit old, but I think it should still work that way.
- Check the smart status of your hard drive. You can do so from your live session. It could be a bad drive.

Besides, 40GB swap sounds excessive, unless you want to hibernate and have 32GB memory.

Edit: Also, BIOS or UEFI?

---

### Post by iRbeastware on 2014-01-13
I have run that check too during these days... no errors spotted, everything seemed fine.

The system has an i7 processor, 16GBs of ram, 1,2 gbs nvidia and the hard disks are SSDs... they are brand new.

On a a sidenote the boot-repair has finally finished scanning the system after 25 minutes... this is what I get : GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again

Should I allocate some memory to "/boot"?? And if 40gbs is way too much for swap, how much would you guys recommend?

edit: BIOS now. tried to run UEFI as install a couple of times also.

edit: I dont even know what I am doing most of the times It's my first week on ubuntu... hence why I am here crying like a baby. but this thing is really getting on my nerves.

To the person who will help me : you will have my deepest appreciations till I pass away... I will remember you my whole life. I could honestly say that I am desperate at this point. I also need to use ubuntu to do some projects.

---

