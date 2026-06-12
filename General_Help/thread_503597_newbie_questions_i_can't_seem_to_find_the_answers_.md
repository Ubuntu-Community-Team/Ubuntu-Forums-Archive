---
title: "newbie questions i can't seem to find the answers to"
date: 2007-07-18
forum: General Help
---

### Post by jayde_drag0n on 2007-07-18
well hello all.. i am very very new to ubuntu (i just installed today) and after a few bugs i am up and running.. but i have a few things i am unsure of how to do... and also i'm so new.. that if i have actually run across the answer.. i probably didn't understand it...

so here is what i want to do

i have a disk drive (well call this Armada) and it is owned by the root (i'm assuming thats typical)
but everything in there is read only.. and that is my music hard drive.. soo i can't change any of the idv tags to reflect genres and such... and its annoying me.. 


second: i had initially tried to install ubuntu on a seperate drive from windows (well call that drive Gaz and my main *now* drive Zim) well it failed miserable.. and i went back to windows.. well i decided to screw it all and wiped windows and installed ubuntu... and now i have my drive Gaz... not labeled with the naming system i wanted ... ie its named 28.7Gig drive.. yuk.. i want it to be called Gaz again... and i want to erase the drive so i can use it for storage.. but once again .. i can't do anything with it because of the whole Root thing again

so basically if someone can give me a STEP BY STEP instruction on what i need to do to resolve my issue i would be eternally gratefull



here are 2 more buggy problems i'm having

i am using LinuxDC++ which i know is still in testing phase... but the issue i'm having there is that while i can browse and get files just fine... no text in chat areas comes up... its just blank
user names show up etc.. but for example when i type !help which should give me a list of available commands etc... the new window pops up.. but its blank.. or i'll type in the room... but i can't see any responses.. and the normal rooom text is absent


GAIM.. when i use the irc room... 
when i PM someone i can see them type.. but they can't see me
and when i type in the room.. i can see my text,.... but i can't see theirs


 so there you go... like i said... anyone who can help me... you are a god
and just be patient... i follow directions very well and i'm nice to boot... just be explicit.. assume i know nothing (which i don't) and give me step by step 

thanks

---

### Post by jayde_drag0n on 2007-07-18
and i'm trying the chown and sudo chown commands in terminal.. but once again.. i don't knwo what i'm doing.. and i'm just guessing at what i'm supposed to type.. please help?? 18 of you have already read this post and noone replied... can i be TOO dumb for this board?

all i need on one of my problems is what to type to change the ownership of drives so that i may edit and delete files at will... i just use them for storage... but it doesn't help me any if i can't modify or do anything with the files in them

---

### Post by jaffamuffin on 2007-07-18
Windows?  Could be your drives are NTFS, and you can only mount them read only (unless you know what you're doing)

Post the output of 

mount 

and 

cat /etc/fstab

and

df -h

---

### Post by sawjew on 2007-07-18
Normally there shouldn't be a problem accessing hard drives or partitions, they should be accessible automatically.  What format is the hard drive you are trying to access?

If you have an NTFS hard drive, the standard format for Windows XP, then you will have read only access by default.  If you are not using Windows at all the best thing would be to reformat your drive as ext3, the most common linux format.  If you reformat the drive as ext3 and reboot you should have read/write access to it.

If you have files you need to keep on the drive and it is NTFS you can enable read/write access by following this guide [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

If you have an ext3 or reiserfs (another common linux format) hard drive you should be able to open a terminal and change to the root directory of your hard drive like this ```
cd /media/YOUR_HARD_DRIVE
```

When you are there you can use the following command to change everything to your ownership ```
sudo chown YOUR_USERNAME:YOUR_USERNAME
```

You can then make sure you have permission to access everthing in the drive like this ```
sudo chmod -R 664
```

For more information on permissions see the following link [https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

Now after you have done this you can rename your partitions using the instructions here [https://help.ubuntu.com/community/RenameUSBDrive?highlight=%28rename%29%7C%28drive%29]("https://help.ubuntu.com/community/RenameUSBDrive?highlight=%28rename%29%7C%28drive%29")

I hope this helps you out, most of us have been in the newbie position before and some of us not so long ago.

Enjoy your  life without Windows and Gates.

Sorry I forgot to mention this.  The easiest way to identify your drives and partitions (their locations and formats) is to use Gparted partition editor.  Just open your terminal and paste in ```
sudo apt-get install gparted
```

You will then find Gparted in the System>Administration menu as 'Gnome partition editor'.

---

### Post by jayde_drag0n on 2007-07-18
wooo!!! problem 1 ... solved!!!! ntfs-config was exactly what i needed

---

### Post by jayde_drag0n on 2007-07-18
ugh i spoke too soon.... i mounted the drives.. then ran ntfs config.. and it gave me an errro wsaying that the logfile was unclean and my only choice was to reboot windows and shutdown properly.... well i don't have windows anymore... and i can't lose the files either... and now i also can't mount the drives.. it says "you are not privileged to mount (name)"

---

### Post by jayde_drag0n on 2007-07-18
jayde@Master:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/GIR type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/hdg1 on /media/disk type ext3 (rw,noexec,nosuid,nodev)

jayde@Master:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=47a4813c-5171-463a-8cdb-85ee4a47302b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=b781127c-711f-4b3f-9530-39863e94ad07 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom2 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdf1 /media/DIB ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/hde1 /media/ARMADA ntfs-3g defaults,locale=en_US.UTF-8 0 0

jayde@Master:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  2.6G   31G   8% /
varrun                252M  212K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  164K  252M   1% /proc/bus/usb
udev                  252M  164K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             298G   54G  245G  18% /media/GIR
/dev/hdg1              27G  2.0G   24G   8% /media/disk
jayde@Master:~$

---

### Post by jayde_drag0n on 2007-07-18
aaaand now i need to take a shower and goto work.. so i'll have to come back to this later... BUT many thanks for starting to help me already.. you rock

---

