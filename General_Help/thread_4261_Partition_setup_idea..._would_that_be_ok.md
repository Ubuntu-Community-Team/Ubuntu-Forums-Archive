---
title: "Partition setup idea... would that be ok?"
date: 2004-11-13
forum: General Help
---

### Post by Monika on 2004-11-13
I'm still very naive about partitioning and dual boot systems and everything...

I had this idea which if it would be possible and safe would I think be very convienient...

So, what if I did a /home partition on FAT32? Would windows be able to see it? Could I make windows see it and be able to write to it? Would windows seeing it and being able to write to it be safe or could windows (I have XP Pro) muck something up?

Could I reformat my /home partition in FAT32 without losing the rest of my Ubuntu system? How could I do it if it's possible?

Are there any disadvantages of having a FAT32 file system in linux?

I mean having a /home partition which I could see and write to from both systems would be extremely convienient for me.
I'm just not sure how safe this is cause I've heard lots about windows liking to muck up linux. Also I'm not sure how to do the windows part of this so that windows would "see" this partition.

---

### Post by HungSquirrel on 2004-11-13
Windows is generally smart enough to detect all NTFS and FAT32 hard disk partitions by itself and to assign them drive letters.  If you make your /home FAT32, Windows will see it fine.

I do not know if it is safe to make /home FAT32.  I've never tried.  That part of your query I will leave to someone much smarter than I.  :)

As for reformatting /home, you can do it if you make a backup.  For example:

```
sudo -s
cd /root
tar -cjf home.tar.bz2 /home
exit
```

That will make a compressed archive of your /home.  Naturally, in this example, your / partition must have plenty of space left over to back up all the space you've used up in /home.

If the used space on /home is large, but smaller than 700MB, I imagine you could burn /home to a CD.

After you have a backup of some sort, format the partition the way you want.  I am assuming you can handle that part.  After it's formatted, extract the backup to the new partition.  In the above example, you would:

```
cd /
sudo tar xvjf /root/home.tar.bz2
```

Or something similar.

---

### Post by TravisNewman on 2004-11-13
And be sure to change your /etc/fstab to reflect the new partition taking over for /home

---

### Post by ynef on 2004-11-13
[QUOTE=Monika]So, what if I did a /home partition on FAT32? Would windows be able to see it? Could I make windows see it and be able to write to it? Would windows seeing it and being able to write to it be safe or could windows (I have XP Pro) muck something up?

Could I reformat my /home partition in FAT32 without losing the rest of my Ubuntu system? How could I do it if it's possible?

Are there any disadvantages of having a FAT32 file system in linux?[/QUOTE]
Answers to your questions, in order:

Windows would be able to see it. It would be able to write to it. It will not muck something up. Windows itself does not allow you to format a (V)FAT partition larger than 32GB, but I've heard reports that it can use it just fine. If your needs call for larger partition size than that, make several partitions and mount them under directories in your user's home directory -- one 32GB partition for movies, one for music, etc... or several for music. Just to be on the safe side.

You'd have to make a backup, as it has already been stated in the thread. You'd then reformat it with the linux command "mkfs.vfat", like so (assuming that /dev/hda4 is the partition to format)
mkfs.vfat /dev/hda4
There are plenty of options which you can find in the manual pages for the program.
Of course you can do this through Windows GUI if you'd rather do it that way.

There are plenty of disadvantages when you use VFAT as a filesystem in Linux.
[list]
[*]**Speed loss** -- VFAT is old, ReiserFS and others are newer and have advanced features which make them much faster
[*]**Journaling** -- VFAT is a non-journaling filesystem, meaning that if the computer loses power the filesystem may be easily corrupted. Also, the error checking process takes a long time to complete.
[*]**No file system level security** -- Linux filesystems all allow you to set permissions on files, allowing you to make your personal files readable to only you. VFAT does not have this feature. If your /home is on VFAT, all users can read each other's files.
[/list]

I wouldn't recommend doing it, but if you think that the advantages are worth the disadvantages, then by all means go for it.

---

### Post by Monika on 2004-11-13
wow, thank you very much for the replies :)

> There are plenty of disadvantages when you use VFAT as a filesystem in Linux.

    * Speed loss -- VFAT is old, ReiserFS and others are newer and have advanced features which make them much faster
    * Journaling -- VFAT is a non-journaling filesystem, meaning that if the computer loses power the filesystem may be easily corrupted. Also, the error checking process takes a long time to complete.
    * No file system level security -- Linux filesystems all allow you to set permissions on files, allowing you to make your personal files readable to only you. VFAT does not have this feature. If your /home is on VFAT, all users can read each other's files.


I wouldn't recommend doing it, but if you think that the advantages are worth the disadvantages, then by all means go for it.

Well, of those three there's one that bothers me... - how easilly can the filesystem be corrupted? I do have one FAT partition on this comp and we have had power cuts and nothing seems to have happened... But I'm wondering how common a problem is this?
I can live with it being a bit slower (advantages outweigh this one) and since I'm the only user of the computer, privacy is not much of an issue. And if I start writing a diary or something like that I think it's possible to set a password in Open Office ;) But losing all the files on that partition... ouch that would hurt... If it was just some files then I'd live, but losing the whole parition.... ouch

---

### Post by HungSquirrel on 2004-11-13
> how easilly can the filesystem be corrupted?
In my experience with Windows on FAT32 filesystems, quite easily.  Almost any time the computer shut off incorrectly, the partition would have errors.  Windows ScanDisk could usually fix it, but it was still risky.

I don't know how well fsck handles the situation, so I cannot comment on it from a Linux standpoint.

---

### Post by poptones on 2004-11-14
The security isn't as much as an issue since you can setup the system to use .htaccess files, .hidden files and such. But from a data integrity standpoint FAT32 is a very, very bad idea. I have lost over 50GB of music and scads of pictures and movies because of a FAT32 partition table getting overwritten (it's really, really easy to do in linux). Even before that it was not at all uncommon to find movies that developed bad spots (or in the case of AVIs just stopped working at all), pictures that became corrupt or disappeared and songs that developed ticks and pops. This was on a drive that is still in use and working just fine under linux using a proper journaling filesystem.

I think the "danger" with windows and linux on the same machine is that sometimes windows doesn't always respect the sequence information of partitions, so if there's some damage and windows does a "recovery" you'll find yourself suddenly unable to get into linux because your fstab information no longer matches. I had this happen myself a few times under mandrake so I know it's not terribly uncommon. 

I suggest getting a small USB drive and setting it up as fat32. That way you won't tend to think of it as "permanent" and so will be less likely to suffer a major loss if the data gets crosslinked or the partition table gets hosed.

---

### Post by anklator on 2004-11-14
i think that its a lil messy puting home partition on a vfat fs, anyways u can mount ur win partition under /home/username/win, an u could keep ur options on a native fs

---

### Post by Monika on 2004-11-16
Thanks for all the input :)
I think I've made a decision about what to do :) I'll stay with an ext3 home partition, but I'll make it quite small 1GB at most, probably less. Will probably mostly be storing documents and such there, maybe some pictures or music but a very limitted amount, I don't tend to download much of those.
And then the rest of the linux space I have I want to format with vfat despite its disadvantages cause I just need to be able to have a partition of about 15GB (for videos) which I need to be able to read and write from both Windows and Linux and some risk of losing data in this case is worth it for me. The files that will be later difficult to replace or that I would reaaally not like to lose, I will back-up somehow, but for most of them it won't be a huge tragedy, just an annoyance (and it's going to be a much bigger annoyance for me to not have a 15GB read and write partition in both Windows and Linux, plus I'm going to use a lot of hard disk space unnecessarily cause then I'll have the same files twice on my computer so instead of 15GB I'll be using 30GB which is extremely silly).

My final question - how do I set out to do this? :) I already have some replies on how to back up my /home partition for which I am thankful - I want to keep all my settings :) And also how to format my entire /home partition, but what do I do to resize my /home partition and then create a new (vfat) one in the free space? :) (without totally reinstalling my whole Ubuntu system of course :) )

Thanks for all your help :)

---

### Post by TravisNewman on 2004-11-16
*phew*
That's a lot of information. Let me see if I get you here.
/home - 1GB ext3
15GB vfat
Your current windows and linux partitions

you can resize ext3 partitions with parted, or the graphical interface QTParted. QTParted acts basically like partition magic. You can use this (or parition magic in windows) to resize and more the partitions as you like, then create the new ones.

---

### Post by Monika on 2004-11-24
Thanks for the help everyone :)

I ended up reinstalling actually... Cause I had no idea how to reinstall GRUB on its own and anyway, since I had a /home partition and I find the manual partition set-up in the Ubuntu installer rather easy to use, it was extremely easy to reinstall. All my settings, bookmarks, launchers... bah even the Ipv6 mozilla bug were as with my previous install, so it was just a question of installing the programs.
But now I have a nice 15GB FAT32 partition which mounts under /fsvideo :mrgreen:

Thanks for the help! :)

---

### Post by ubuntu_demon on 2004-11-24
Is read/write mounting ntfs in linux safer than using VFAT ?

---

### Post by Monika on 2004-11-26
Depends what you want to do :)
If all you need is read access to your Windows files in Ubuntu and do not need Windows to see any files you make in Ubuntu, then mounting ntfs is probably all you need. But if you need read and write access from both systems then fat is probably the only thing you can do. Apparently it is possible to write to ntfs partitions from linux, but it's at an experimental stage and you risk damaging your ntfs data.
And so far, so good, nothing's happened to my fat data :mrgreen:

---

