---
title: "CAN'T PLAY cdS"
date: 2008-05-29
forum: General Help
---

### Post by mahmater on 2008-05-29
hello everybody,

since my hardy installation I haven't been able to play CDs and when I access the CD drive from: places ____computer, and click on it it just says: UNABLE TO MOUNT LOCATION. CAN'T MOUNT FILE. what's up?
 it seems that it needs root permission to work.how can I manage that?
  I would like also to inquire a/t the way to make CDs launch automatically upon insertion...many thanks.

---

### Post by alzwded on 2008-05-31
Don't know if it will actually work, but for the sake of trying reconfigure the nautilus package. Haven't done this before in ubuntu and i don't know how to reconfigure stuff with the apt package management, but ask around.

Or, check your fstab if it is the same, it should have the line
/dev/hdc /media/cdrom0 urdf,iso9660 user,noauto,exec 0 0

Or check your /dev/hdc file permissions and see that they are 0660 and the owner is root and the group is cdrom and that your user is in the group cdrom.

Then again, it could always be a bug - search on launchpad for the symptoms

---

### Post by Black_Monkey on 2008-05-31
I have a similar problem, and in my fstab there is:
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
(note: no "exec" there).
However, /dev/hda does not exist :-S

---

### Post by mc4man on 2008-05-31
> However, /dev/hda does not exist
run this and see what is there
```
sudo lshw -C disk
```

---

### Post by Black_Monkey on 2008-05-31
```
*-disk
       description: ATA Disk
       product: Maxtor 6L200P0
       vendor: Maxtor
       physical id: 0.1.0
       bus info: scsi@4:0.1.0
       logical name: /dev/sda
       version: BAJ4
       serial: L41L0RYH
       size: 189GiB (203GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=07cc07cc

```

But isn't that the harddrive? That works fine, it's the CD drive that's having problems.

---

### Post by mc4man on 2008-05-31
that command would show all your drives, doessn't appear the drive is being detected. you could look thru your system logs and see (debug, messages, syslog)  or try 
 ```
grep 'CD-ROM' /var/log/dmesg
```,  ```
grep 'CD-ROM' /var/log/debug
```  ```
grep 'CD-ROM' /var/log/syslog
``` and see if anything shows up

edit have you tried booting up with a cd (any kind) in drive?

---

### Post by Black_Monkey on 2008-05-31
Nope, none of those return anything.

---

### Post by mc4man on 2008-05-31
I would try booting up with an audio cd in drive and see if drive is detected or booting to live cd and see if you can. If not  ck. in bios setup and see if a cd-rom reader is shown as a drive

---

### Post by mahmater on 2008-05-31
thanx 4 reply. now here is what fstab returns:
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0    
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0      

and here's the output of :  sudo lshw -C disk

-cdrom:0
       description: CD-R/CD-RW writer
       product: CD-RW GCE-8527B
       vendor: HL-DT-ST
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.02
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM SD-M1502
       vendor: TOSHIBA
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1Y08
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
 when I right click on the cd drive to see what kind of permission there is it just says : permission not determined!

now can u just figure out what's the matter?

---

### Post by alzwded on 2008-06-02
Well... if your fstab has /dev/hda for a cdrom and it doesn't work just try replacing it with /dev/cdrom or /dev/scd0. 
Or if it still doesn't work try booting from the livecd and after that check the /etc/mtab for a line containing cdrom and see how it detects your drive.

---

### Post by mahmater on 2008-06-03
indeed friend I discovered out of the blue that not only my CD Rom drives but also the windows partitions can't mount/work with no apparent reason.
cannot mount disk. permission not determined!!!!!!!!!!
I haven't played any CD for 10 days now!

---

