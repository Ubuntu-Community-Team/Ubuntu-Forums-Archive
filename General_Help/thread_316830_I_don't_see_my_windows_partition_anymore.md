---
title: "I don't see my windows partition anymore"
date: 2006-12-11
forum: General Help
---

### Post by PrinceArithon on 2006-12-11
Ok, I have my system set up so I can see my windows partition and a fat32 partition on my desktop here in Linux.  Everything worked fine friday.  I took a break away from my computer saturday, and sunday when I went on my windows partition was gone from my desktop.  When I went to places > computer.  It wasn't there either.  So I went to places > computer > filesystem > media and clicked into the windows folder all I seen was a blank folder.

I have no idea what it could have been except for an update of a program that came friday night when I was last on.

Anyway I'm not sure how to go about and fix this, does anyone have any idea what is wrong??  LOL I already know....what is wrong is that Windows is on my system in the first place LOL.  Seriously though does anyone know what I can do??

---

### Post by taurus on 2006-12-11
What does your /etc/fstab look like anyway?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
df -h
```

---

### Post by PrinceArithon on 2006-12-11
here are my outputs

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 -- converted during upgrade to edgy
UUID=dfab9928-7e46-4123-82ac-ba01c06c3968 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=3e4d8662-2dd4-4b03-9ec3-5ec47449209a none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda1   /media/windows    ntfs-3g    defaults,locale=en_US.utf8   0    0
/dev/sda5   /media/fat_files vfat  iocharset=utf8,umask=000  0    0



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              37G   22G   14G  62% /
varrun               1014M   96K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
procbususb             10M  148K  9.9M   2% /proc/bus/usb
udev                   10M  148K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   18M  997M   2% /lib/modules/2.6.17-10-386/volatile
/dev/sda5              15G  590M   15G   4% /media/fat_files

---

### Post by taurus on 2006-12-11
I see that /dev/sda5 is mounted but not /dev/sda1!  What happens if you run this command from the terminal and see if /dev/sda1 is mounted this time?

```
sudo mount -a
df -h
```

---

### Post by PrinceArithon on 2006-12-11
I got something interesting..here it goes:  

Failed to mount '/dev/sda1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              37G   22G   14G  62% /
varrun               1014M   96K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
procbususb             10M  148K  9.9M   2% /proc/bus/usb
udev                   10M  148K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   18M  997M   2% /lib/modules/2.6.17-10-386/volatile
/dev/sda5              15G  590M   15G   4% /media/fat_files


Now I do have a possible idea as to what might be the problem.  I was playing GTA San Andreas and I left the controller I was using plugged into the USB port when I reset the computer and went back into Linux.  It could be I might just need to load Windows once so that way it realizes the controler is gone and then go back to Linux to see if it works or not.  I'm just not sure and don't want to waste my time playing with that if it doesn't work..  What do you think should be done??

---

### Post by taurus on 2006-12-11
And while you are in XP, check the integrity of the drive too, /dev/sda1...

---

### Post by PrinceArithon on 2006-12-11
I checked it, and even done some tests and still nothing worked.

---

### Post by PrinceArithon on 2006-12-11
bumping it back up

---

