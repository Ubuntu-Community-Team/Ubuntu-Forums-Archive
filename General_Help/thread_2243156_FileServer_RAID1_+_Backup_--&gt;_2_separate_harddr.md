---
title: "FileServer RAID1 + Backup --&gt; 2 separate harddrives"
date: 2014-09-06
forum: General Help
---

### Post by danhansendenmark on 2014-09-06
[HR][/HR]                                                                   Hi,


I've been building a FileServer with RAID1 (Ubuntu Software RAID). No  problems there! But, I want to better this server, so that it makes  backups as well. Therefore I've bought 4 new WD drives, 2 x 2Tb and 2 x  1Tb.

I want to use the 2 x 2Tb drives for RAID1 with the OS, swap etc. and  then use a CRON command to "copy" the content of the fileserver RAID1 to 2  separate drives. (1 copy on each 1Tb harddrive) 2 drives to be double sure ;)

What I need is:
1. The command to copy all the content of the RAID1 (except the system  files) to both "extra" harddrives. I'm guessing the CRON daily is the  place where this file needs to be located.
It must be something like: 
     Code:
     #!/bin/sh

cp -r md1/data/* sdc  
cp -r md1/data/* sdd 

done 
2. Maybe cp -a  is a better argument?

3. Will the first command line be executed before the next? Or will it  just execute both right away? I'm guessing the last one. How can I make  it, so that the first copy will be done, before the next starts?? Is it  possible??

4. Which filesystem will be the best for these 2 extra backup harddrives?  It's a mixed environment! Files from NTFS systems and from Ubuntu  Desktop & Ubuntu Server as well!! Maybe ext4 ??

It's my first CRON command/setup, so if you've got some knowhow you want to share with me, please don't hesitate to tell me [IMG]http://www.howtoforge.com/forums/images/smilies/wink.gif[/IMG]
Sorry for this newbie question [IMG]http://www.howtoforge.com/forums/images/smilies/redface.gif[/IMG]

Have a nice weekend [IMG]http://www.howtoforge.com/forums/images/smilies/wink.gif[/IMG]         


Kind Regards,
Dan/Denmark

---

### Post by gordintoronto on 2014-09-07
EXT4 is always a good choice as a Linux filesystem.

Have you looked at rsync?

---

### Post by nerdtron on 2014-09-07
rsync might be the tool for you.
Here's a tutorial [http://www.howtogeek.com/135533/how-to-use-rsync-to-backup-your-data-on-linux/](http://www.howtogeek.com/135533/how-to-use-rsync-to-backup-your-data-on-linux/)

Rsync is basically cp (or scp) but with steroids. It can copy files from local machine to another remote machine via ssh. It can copy between local directories too. The basic syntax:
```
rsync -[options] [source] [destination]
```

You can try something like this on the terminal:
```
rsync -avrh --progess /home/username /mnt/backupdrive/username
```

-a means copy the attributes such as ownership and permissions of files
-v for verbose output
-r for recursive, copying folders and its contents
-h for human readable format of numbers
--progress to show the progress of the transferring

Another good thing about rsync is that it is **resume-able**. You can cancel an existing transfer midway and when you run it again, it will scan the files already on the destination and will only send the missing files.

---

### Post by danhansendenmark on 2014-09-10
Hi both of you ;)


Thanks for your response! Rsync sounds just great. I'm reading about it and has finished putting the hardware together.
The --progress argument sounds good! And I can see that -a is indeed needed in my case, but I'm not sure about the compression nor am I sure about password encryption. To begin with I wanted the copies/backups to be accessible, but now I'm not so sure. Back in the old days I used RAR in a windows environment and encrypted my data and had RAR make me backups in sizes which fitted a DVD. For now it's from one disk (md) to another, so maybe I don't need that much security. What's important to me is the data. Can't risc loosing them and if both discs in the array should crash, then I have data on the 2 backup drives. If theese should crash I've got the possibility to do datarecovery on these drives. This is why I'm using standard harddrives for this instead of SSD. 
I'm attending University and my work will be on this fileserver along woth everything else. It's Rack-mounted systems in 2U chassis/cases, so it's not much I look at them. It just has to work, so I don't have to worry ;) I'm going to activate the RAID Monitor Deamon of course, and I've done some temperature watchdog scipts for CPU/GPU and HDD as well. So maybe I'm somehow safe, I certainly hope so ;) 

Right now it's a fileserver with SAMBA so I just map to gain access to data. Along the way I would like my desktops Linux/windows to make backups directly to this fileserver using the ssh connection, it sounds really great! There will be files I wan't to keep. There's almost always something at the desktop. 

What would you do with the data backups? Would you password encrypt? compress?

Again, thanks for your help!

Kind Regards,
Dan/Denmark

---

### Post by nerdtron on 2014-09-11
>  What would you do with the data backups? Would you password encrypt? compress? 

How big is you data? and what type of files are they? How long would you like them to keep?

If you have lots of for example: documents, emails, htmls, then you probably want to have them on a folder and then compress them.
If your data are mostly videos and music files then you won't benefit with compression at all.

Encryption -- depends if you really want to secure your data, but for home use I don't think you need the extra step. 

Backups/archives should be stored on a separate machine (at least to be safe). It doesn't have to be SSD, just BIG storage.

That said it is still up to you on what you on what you want to do with you backup.

---

