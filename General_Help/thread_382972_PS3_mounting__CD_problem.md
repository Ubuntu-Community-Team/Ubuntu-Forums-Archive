---
title: "PS3 mounting  CD problem"
date: 2007-03-12
forum: General Help
---

### Post by ATT-Half on 2007-03-12
I'm going to copy my problem from  HOWTO: Install Ubuntu on PS3 from Live CD  see if i can get help here cause i think that thread is dead

having problems accessing my DVD/CDROM drive

here my fstab & mtab

```
# /etc/fstab: static file system information.
# file system mount point type options dump pass
LABEL=/ / ext3 defaults 0 0
LABEL=/boot /boot  ext2 defaults 0 2
LABEL=SWAP SWAP swap sw 0 0
proc /proc proc defaults 0 0
sys /sys sysfs defaults 0 0
/dev/fd0 /mnt/floppy auto noauto,rw,sync,user,exec 0 0
/dev/cdrom /mnt/cdrom iso9660 noauto,ro,user,exec 0 0
###### /etc/fstab done
```



```
/dev/sda3 / ext3 rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sda1 /boot ext2 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
```

everytime i insert a DVD it tells me mount: mount point /mnt/cdrom does not exist
even the livecd that was use to install tells me that
so it's not like it's having problems reading the media
when in kboot promt i enter fdisk -l it only shows sda partitions ext2 ex3t swap

i did allow my user cdrom access + external storage devices if that helps
i even tried to edit this line on fstab
/dev/cdrom /mnt/cdrom iso9660 noauto,ro,user,exec 0 0
to /dev/sr0 /mnt/cdrom iso9660 noauto,ro,user,exec 0 0
but nothing anyone know what's goin on ?

thx


> 2nd post: after few hours trying to figure out my self

well i was googleing looking for solutions but much of content out there is not for PS3. found out about mac-fdisk and i confirm it to be install when i check package manager but neither
fdisk -l or mac-fdisk -l work can't tell if it's been detected or not and what path.

i can sudo them all i want nothing

only in the kboot prompt does fdisk - l work which list 3 mian sda patitions
dam everything when perfect aside from this am already running anime with vlc & mplayer USB sticks even mount fine haven't tried CF or SD yet.

anyone help me

could KDE have taken something related to CDROM/DVD when i uninstall it

> 3rd post after after another 6 hours


well i got it to work but not working properly


what i did play with cdrom mount commands but always come back
mount mount point mnt/cdrom not found

i when to fstab and deleted
```
/dev/cdrom /mnt/cdrom iso9660 noauto,ro,user,exec 0 0
```

this time fstab was not in the way & now terminal return with:
you need root privileges to run mount /dev/cdrom /mnt/cdrom
:) 
tried sudo mount /dev/cdrom /mnt/cdrom
got this back
did not provide file system will try udf
mnt/cdrom do not exist
but it still it mounted:) 

when on to play my few files after while i come back (disc still in drive)

so i figured now  to find a way to automate mounting using the command i found without going to terminal every time

keep trying mount commands in one those cases i think i mistype something
i think i got list of all mount options i think

so there i read something about labeling the dev/sda -L
so i remember when installing linux i had to label sda partitions
an figure i'll give it tray with cdrom

but made mistakes here


```
i open a terminal window
sudo /dev/cdrom -L "/cdrom
hit enter
i forgot to close with " so i did again 
sudo /dev/cdrom/ -L "/cdrom"
```

hope this doesn't make double /cdrom cause have no clue of the delete command for label's

well kinda forgot about it  since i don't know the remove label command if that's even posiible
when on back to fstab

and figure i give it a try to mix/match somewhat like ext3 and boot lines with but using cdrom
LABEL=/ / ext3 defaults 0 0
LABEL=/boot /boot ext2 defaults 0 2

and i enter this LABEL=cdrom /mnt cdrom iso9660 noauto,ro,user,exec 0 0

well much to my surprise it worked but now i got a problem it won't eject ](*,)
so i got up and tried ps3 eject button won't work.
after testing i figure out a way to eject by right clicking mounted DVD icon and press eject then i have to get up walk to ps3 and press the eject button to finally eject.


can someone help you can't say i didn't put effort
linux nOOb signing off

how do i got about fixing all this 
:grin:

---

### Post by ATT-Half on 2007-03-13
I figure it out :guitar: 

i reset my fstab file to default settings although not sure how to remove label that i made on /cdrom but hey now it's working.

all i needed to do was:

sudo mkdir /mnt/cdrom

8-) 

just in case somehow someone gets the same problem there your fix

---

