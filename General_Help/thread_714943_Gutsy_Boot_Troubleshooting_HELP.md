---
title: "Gutsy Boot Troubleshooting HELP"
date: 2008-03-04
forum: General Help
---

### Post by thuston88 on 2008-03-04
I _WAS _running Gutsy on a Dell laptop with no problems.  I dual boot it with XP.  Suddenly it will not boot after I tried to update it at the prompt of the Update Manager.  I end up with a long scrolling screen of text before it just stops and hangs.  Hardware is all compatible since it was working fine before.  XP continues to run OK (at least for Windows).

Can someone direct me to a good method to systematically troubleshoot this?  Is there a description of what loads first, second, etc. so that I can see if something is corrupt?  Does the text displayed on the screen during boot get saved to a file somewhere that I can get to the beginning of the error messages?  Is there a way to roll back the update?  I hate to wipe it out and start over since I had Compiz Fusion and Kibadock up and running just fine.  And they were a major time investment to get working!

Any help or suggestions will be appreciated.  Thank you.

---

### Post by jeffus_il on 2008-03-04
Can you post the last few rows of text before the hang?

---

### Post by thuston88 on 2008-03-04
When starting Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) the final display is:

ALERT! dev/disk/by-uuid/23a42298-f9ef-4321-928a-2dd6b51aa536 does not exist

Dropping to a shell!

Check your root= boot argument (cat /proc/cmdline)

Check for missing modules (cat /proc/modules), or device files (ls /dev)

(initramfs)


at this point it hangs.  are these items I can check with a live dvd?  What boot arguments or modules am I looking for?

Thanks for any help!

---

### Post by jeffus_il on 2008-03-05
Grub, the boot loader is not finding your boot partition on your hard disk. If you know the partition name, you can edit the grub menu and boot. I can post how to do this. The easiest way is to download "supergrubdisk" burn it to a CD, and boot from the CD. SuperGrubDisk knows how to fix this error and also boot you computer.

---

### Post by thuston88 on 2008-03-06
I still cannot boot Gutsy.  I ran SuperGrubDisk but it did not help.  Same results.  

I used the LIVE disk to see that my root partition was sda6.  I edited the command line to:  boot= /dev/sda6 and got:  ALERT /dev/sda6 does not exist.  Is that format correct for GRUB?

I also looked at /proc/cmdline and /proc/modules.  They both exist but are empty, 0 bytes.  Is there something I can find and copy into these that is required to kick start this thing?

I appreciate any help.  It looks like everything is on the root partition but it will not boot into it.

Thank you.

---

### Post by jeffus_il on 2008-03-06
Can you post the output of the following?
```
parted
```then
```
p
```

in a terminal after booting from the livecd?

---

### Post by thuston88 on 2008-03-06
Here is my partition table:


GNU Parted 1.7.1

Using /dev/sda

Welcome to GNU Parted! Type 'help' to view a list of commands.
  
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B

Partition Table: msdos

Number  Start      End       Size        Type       File system   Flags

 1           32.3kB   32.9MB  32.9MB  primary   fat16             

 2           32.9MB  18.1GB  18.0GB  primary    ntfs             boot 
 
 3           18.1GB   60.0GB  41.9GB  extended               lba  

 5           18.1GB  42.7GB  24.7GB   logical      ntfs              

 6           42.7GB  48.0GB  5239MB  logical      ext3              

 7           56.0GB  59.2GB  3183MB  logical      ext3              

 8           59.2GB  60.0GB  806MB   logical       linux-swap        


My Linux / is on sda6 and the /home folder is on sda7.

---

### Post by jeffus_il on 2008-03-07
> **thuston88 said:**
> Here is my partition table:


```
GNU Parted 1.7.1

Using /dev/sda

Welcome to GNU Parted! Type 'help' to view a list of commands.
  
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B

Partition Table: msdos

Number  Start      End       Size        Type       File system   Flags

 1           32.3kB   32.9MB  32.9MB  primary   fat16             

 2           32.9MB  18.1GB  18.0GB  primary    ntfs             boot 
 
 3           18.1GB   60.0GB  41.9GB  extended               lba  

 5           18.1GB  42.7GB  24.7GB   logical      ntfs              

 6           42.7GB  48.0GB  5239MB  logical      ext3              

 7           56.0GB  59.2GB  3183MB  logical      ext3              

 8           59.2GB  60.0GB  806MB   logical       linux-swap        
```
My Linux / is on sda6 and the /home folder is on sda7.
reformatted...

---

