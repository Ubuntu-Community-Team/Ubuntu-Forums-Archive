---
title: "Partimage VS Clonezilla?"
date: 2019-04-16
forum: General Help
---

### Post by josaphat2 on 2019-04-16
Here's a recap :

[SIZE=4]**Partclone GUIs (Apart-GTK and Clonezilla)**[/SIZE]

Just trying out apart-gtk, it only output one file.

it is much more convenient specially if you have ubuntu on USB stick (which I do).

You can do other stuff while partclone does it job on the background. But that would risk the integrity of the backup file won't it?

Might be good for a more frequent backups (sort of like Windows' system restore, but I figure the image files would be humongous).

While Clonezilla can be used for long term backups with all the configuration of the backup editable in plain text format out of the box.


Also apart-gtk is very good for beginners, definitely. No-nonsense, clean and very simple interface.

Both uses partclone, but I figure they're not compatible with one another. The output file is definitely very different from each other.


Both has its ups and down. For longer term, I'd stick to Clonezilla for now. As this program kept being updated to this second. My Clonezilla backup years ago still usable today and interchangeable.

Installing clonezilla within Ubuntu works sometimes ago, but I don't know why it won't run now (errors when mounting partition). But the live CD works anyway.

Apart's fate is still unknown. But I do wish it will be merged into Debian and Ubuntu's official repository though.


[SIZE=4][B]Clonezilla
[/B][/SIZE]
When making this thread and maintaining it, I relearned why I did choose clonezilla in the first place. It was part of a bigger project, called DRBL (Diskless Remote Boot in Linux).

I'm imagining you can deploy 1 image to multiple nodes over the network, if you can work it out.

But being part of that bigger project is making Clonezilla a bit more difficult to set up within a distro.

so in Ubuntu/debian you need to setup drbl servers properly first.

Me? So far I'm still using local computers, so the live cd would be enough.


[SIZE=4]**FS-archiver**[/SIZE]

As for fs-archiver, there's steep learning curve to get pass through specially the CLI commands. I couldn't risk any backup if I put in the wrong options.

The qt5-fsarchiver interface suddenly mounts all my partitions available. Kinda scary to me.

But I'm keeping it since most of the posts here favor it.


**[SIZE=4]Partimage[/SIZE]**

Partimage? Mmm I don't know. It got a bit friendlier ncurses interface than Clonezilla do.

WMC saying that it doesn't support NTFS which is definitely a dealbreaker for me.


[SIZE=4]**Conclusion**[/SIZE]

I just wish somebody put in together Clonezilla and Gparted within one live distro. The closest thing you'll ever get is System Rescue CD, which it got partimage instead of clonezilla.

Eh there's Parted Magic, but then again I already had both live isos (gparted and clonezilla) working in my USB, and both are free while Parted Magic uses subscribtion fee.

BTW thanks for the input, guys.

---

### Post by VMC on 2019-04-16
Partimage doesn't support **[ext4]("http://www.partimage.org/Supported-Filesystems/")**.


[Partclone]("https://partclone.org/") does support ext4.

Also Clonezilla will clone using only one file if you make the file range larger. It states that when you clone.

I mostly now use [fsarchiver]("http://www.fsarchiver.org/"). Only use partclone/clonezilla if backing up NTFS fs.

---

### Post by monkeybrain20122 on 2019-04-16
I recommend [fsarchiver]("http://www.fsarchiver.org/"). It is more flexible than clonzilla as it doesn't require the target partition to be as big as the source even if the source might be mostly empty. This is a show stopper for me as I sometimes clone my os to transfer it to different machines and there is no reason why the targets would have a hard drive as big as the source machine. fsarchiver also supports live cloning which means using the machine when copying happens in the background. It is in the repo.

There is also a [gui]("https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver"), though not as flexible as the command line tool (e.g you can exclude directories and files with command line but can't do it with the gui)

---

### Post by VMC on 2019-04-16
> **monkeybrain20122 said:**
> ...There is also a [gui]("https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver"), though not as flexible as the command line tool (e.g you can exclude directories and files with command line but can't do it with the gui)
That "gui" is interesting. It somehow compresses better than stock fsarchiver. I don't use it much but just the same it interesting. I have a script for fsarchiver to backup my several linuxes.

---

### Post by HermanAB on 2019-04-17
+1 for fsarchiver

---

### Post by mastablasta on 2019-04-17
best GUI i saw so far was made in RedoBackup. unfortunately the software is no longer supported. I think it was using partclone under it, however the GUI was super easy to use and worked like a charm on windows as well as on linux. this is when backing up partitions and full disks. 

clonezilla interface is clunky. if you make a "mistake" you have to go through it again. Redobackup had a nice wizzard you could move through. 

anyway i think backup tool should be reliable and easy to use, so that more people would feel normal about backing up their data at least with some snapshots / images if they are not bothered by daily backups.

edit: looks like someone is making a new GUI for partclone called apart: [https://github.com/alexheretic/apart-gtk](https://github.com/alexheretic/apart-gtk)
looks simple to use.

---

### Post by josaphat2 on 2019-04-18
Just heard about partclone here. Also FSarchiver.

So most voted for FSarchiver

The feature that attract me to Clonezilla is that I can actually restore the image to different partition also with different size (can be smaller but it warns me about it).

I did this quite long time ago, moving my whole linux installation from my laptop to my desktop. It works without problem (but it does require a bit of tinkering though).

All the configuration files are provided within the backup image folders.

Can FSarchiver do that?

Also partclone's GUI above is pretty attractive. It's very simple and no-nonsense or whatsoever.

Hopefully someone upstream to the official repository.

---

### Post by mastablasta on 2019-04-18
> **josaphat2 said:**
> 
The feature that attract me to Clonezilla is that I can actually restore the image to different partition also with different size (can be smaller but it warns me about it).


don't know about fs archiver, but part clone should be able to do it. i know redo backup did it, though i never tried to restore image to smaller partition.

---

### Post by VMC on 2019-04-18
That CZ feature is new to me:
[https://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/advanced/09-advanced-param.php](https://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/advanced/09-advanced-param.php)

Also, yes fsarchiver will restore to smaller partition as long as the data will fit, which only makes sense.

---

### Post by josaphat2 on 2019-04-19
> **mastablasta said:**
> don't know about fs archiver, but part clone should be able to do it. i know redo backup did it, though i never tried to restore image to smaller partition.

I was just backing up my drive.

Clonezilla IS based off partclone. I just realize that myself. when doing stuffs, it reads "parclone blahblahblah" I can't remember.

Probably Clonezilla project is actually just the ncurses-gui for partclone.

---

### Post by josaphat2 on 2019-04-19
> **VMC said:**
> That CZ feature is new to me:
[https://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/advanced/09-advanced-param.php](https://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/advanced/09-advanced-param.php)

Also, yes fsarchiver will restore to smaller partition as long as the data will fit, which only makes sense.

Sweet! Thanks!

---

### Post by VMC on 2019-04-19
This is the way CZ works. I copied it while in progress. Made my own script [X=partition to clone, use gzip if pigz not installed]:
```
sudo ./partclone.ext4 -z 10485760 -N -c -s /dev/sdaX -o - | pigz -c --fast -b 1024 -p 16 > /FILELOCATION/ubuntu.gz ; cat /FILELOCATION/ubuntu.gz|pigz -d -c|sudo ./partclone.chkimg -N -s -
```
to Restore:
```
zcat /FILELOCATION/ubuntu.gz|sudo ./partclone.ext4 -N -r -o /dev/sdaX
```

---

### Post by josaphat2 on 2019-04-20
Here's a recap :

[SIZE=4]**Partclone GUIs (Apart-GTK and Clonezilla)**[/SIZE]

Just trying out apart-gtk, it only output one file.

it is much more convenient specially if you have ubuntu on USB stick (which I do).

You can do other stuff while partclone does it job on the background. But that would risk the integrity of the backup file won't it?

Might be good for a more frequent backups (sort of like Windows' system restore, but I figure the image files would be humongous).

While Clonezilla can be used for long term backups with all the configuration of the backup editable in plain text format out of the box.


Also apart-gtk is very good for beginners, definitely. No-nonsense, clean and very simple interface.

Both uses partclone, but I figure they're not compatible with one another. The output file is definitely very different from each other.


Both has its ups and down. For longer term, I'd stick to Clonezilla for now. As this program kept being updated to this second. My Clonezilla backup years ago still usable today and interchangeable.

Installing clonezilla within Ubuntu works sometimes ago, but I don't know why it won't run now (errors when mounting partition). But the live CD works anyway.

Apart's fate is still unknown. But I do wish it will be merged into Debian and Ubuntu's official repository though.


[SIZE=4][B]Clonezilla
[/B][/SIZE]
When making this thread and maintaining it, I relearned why I did choose clonezilla in the first place. It was part of a bigger project, called DRBL (Diskless Remote Boot in Linux).

I'm imagining you can deploy 1 image to multiple nodes over the network, if you can work it out.

But being part of that bigger project is making Clonezilla a bit more difficult to set up within a distro.

so in Ubuntu/debian you need to setup drbl servers properly first.

Me? So far I'm still using local computers, so the live cd would be enough.


[SIZE=4]**FS-archiver**[/SIZE]

As for fs-archiver, there's steep learning curve to get pass through specially the CLI commands. I couldn't risk any backup if I put in the wrong options.

The qt5-fsarchiver interface suddenly mounts all my partitions available. Kinda scary to me.

But I'm keeping it since most of the posts here favor it.


**[SIZE=4]Partimage[/SIZE]**

Partimage? Mmm I don't know. It got a bit friendlier ncurses interface than Clonezilla do.

WMC saying that it doesn't support NTFS which is definitely a dealbreaker for me.


[SIZE=4]**Conclusion**[/SIZE]

I just wish somebody put in together Clonezilla and Gparted within one live distro. The closest thing you'll ever get is System Rescue CD, which it got partimage instead of clonezilla.

Eh there's Parted Magic, but then again I already had both live isos (gparted and clonezilla) working in my USB, and both are free while Parted Magic uses subscribtion fee.

BTW thanks for the input, guys.

---

### Post by monkeybrain20122 on 2019-04-20
> **josaphat2 said:**
> 

I did this quite long time ago, moving my whole linux installation from my laptop to my desktop. It works without problem (but it does require a bit of tinkering though).

All the configuration files are provided within the backup image folders.

Can FSarchiver do that?



Yes, that is what I use it for.

> As for fs-archiver, there's steep learning curve to get pass through  specially the CLI commands. I couldn't risk any backup if I put in the  wrong options.

There are just two commands savefs and restfs, the options you likely will find useful are -v (verbose) -a -A (live cloning) -exclude=...

---

### Post by josaphat2 on 2019-04-23
> **monkeybrain20122 said:**
> Yes, that is what I use it for.



There are just two commands savefs and restfs, the options you likely will find useful are -v (verbose) -a -A (live cloning) -exclude=...

Thanks.

Still, even though the ncurses interface are very quirky, I'm much more comfortable with Clonezilla atm.

With this thread, I found another partclone front end, Apart-GTK which also means developers seems to favor partclone more, evidently by how many incarnation of partclone's front-end/interface out there.

besides, DRBL should be enough encouragement for someone to further learn about the whole package.

---

