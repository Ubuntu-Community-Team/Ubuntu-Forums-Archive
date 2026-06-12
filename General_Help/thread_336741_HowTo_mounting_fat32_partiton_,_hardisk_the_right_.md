---
title: "HowTo mounting fat32 partiton , hardisk the right way!"
date: 2007-01-12
forum: General Help
---

### Post by fokuslee on 2007-01-12
I am writing this guide b/c i myself had to go through so much to mount it right.  maybe this will help u too!  Oh  Jussi Kukkonen, bettlebrox, goatflyer and un_operatuer on IRC thx again : ) 
To resize/make/reformat your partition to fat32 checkout a program called gparted and gparted live cd. Ok for the good stuff 

first thing we need to check what device host the fat32 partition 
code: fdisk -l | grep FAT32
u can also check with 
code: df -t vfat 
This should return something like /dev/sd(some letter)(some number) for me it is /dev/sda3, if you have pata it will be hd(some letter)(some number)  

Now you want to think about a directory where you want to mount your partition 
for me i picked /media/unsorteddls 
but the unsorteddls folder is not created yet so i need to 
code: cd /media 
code: sudo mkdir unsorteddls

Now you have to find out the uid (user id) and gid (group id) the system assigned you.  
code: id 
Write down the uid=(number)yourlogonname and gid=(number)yourlogonname
for me its uid=1000(fokuslee) gid=1000(fokuslee)

Now i have the device i want to mount and the mount point (folder i just made) and my uid, gid, i go ahead with editing my fstab (file system table)  at /etc/fstab
code: sudo nano -w /etc/fstab
at the end of the file append

/dev/sda3 /media/unsorteddls vfat iocharset=utf8,umask=000,uid=1000,gid=1000 0 0 

u need to substitude unsorteddls uid and gid with ur own unique ones.  vfat tells the system file type is fat32   iocharset has to do with filename encoding Windows uses utf16 so utf8 is the best match.  umask=000 set wrx for owner group and others.   uid=1000, gid1000 set the owner to be myself Not Root.  This is important if you want torrent client to dl directly into the fat32 partition.  0  0 are for dump and fsck options.   To my best knowledge its set to 0 b/c they are not needed for fat32 (someone correct me on this) 

Note you don't need to chmod 777 to the mountpoint b/c umask overwrites chmod

then to make sure ur volume is visible on desktop 
code: gconf-editor 
goto Apps>Nautilus>Desktop
check the box labelled "Volumes Visible"

and Finally 
code: mount /dev/sda3(or wutever ur partition/drive is called)

---

