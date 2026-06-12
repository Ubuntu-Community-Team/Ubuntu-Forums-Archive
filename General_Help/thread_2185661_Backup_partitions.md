---
title: "Backup partitions"
date: 2013-11-03
forum: General Help
---

### Post by Luc_Lacombe on 2013-11-03
Hello

I have a dual boot system with Ubuntu and Win XP.
I would like to backup my main complete Ubuntu partitions on another (NTFS) partition.
The whole complete partition... not the "Home" which is suggested by the included Ubuntu backup softare called "Backup".
In Xp I have Acronis True Image that does the job exactly as I would for Ubuntu.
Can this kind of backup job be done for Ubuntu partition by "Backup" or you would suggest another backup software?
Thanks.

Luc Lacombe (Ubuntu newbie...)

---

### Post by Mark Phelps on 2013-11-03
You have at least a couple of different choices:
1) clonezilla -- more difficult to use, but lots of options you can choose
2) RedoBackup -- very easy to use, but not so many options.

---

### Post by Luc_Lacombe on 2013-11-04
[I][B]Hello Mark

Thanks for help!
I checked both of your suggestions.
Redobackup seemed interesting as it does the simple thing I need.
The only "add-on" thing I need is a software that would be the equivalent of the Acronis True Image's feature which is called _Archive/mount_.
This is the creation of a virtual disk mounted in Nautilus, from which you can copy/paste to your main Home folders.
Do you have any suggestions?
Thanks!

Luc Lacombe[/B][/I]

---

### Post by leclerc65 on 2013-11-04
Redo is very buggy.

---

### Post by Luc_Lacombe on 2013-11-04
[I][B]Ok but what do you have to suggest instead?

LL[/B][/I]

---

### Post by speartip on 2013-11-04
Clonezilla isn't too difficult to use.
You can download a copy from here:
[http://clonezilla.org/downloads/download.php?branch=stable](http://clonezilla.org/downloads/download.php?branch=stable)
Just burn the iso to disc & boot from the disc. Just read the onscreen options carefully. I have cloned partitions numerous times & restored them without any problems. The only restriction is that the partition you restore to must be at least equal or greater in size than the clone.
If you have any issues or questions just post back.

---

### Post by Luc_Lacombe on 2013-11-04
[I][B]Hello Speartip

Thanks for suggestion.
I downloaded Clonezilla and burn the ISO.
I booted and frankly...it's too complicated and for nothing.
I don't understand this.
25 years ago everything was complicated but with evolution software are to become easier.
Which is not the case here.
Not that I am not competent or have no patience but I have to put energy elsewhere in my duties.
Anything else to suggest?

Luc[/B][/I]

---

### Post by Mark Phelps on 2013-11-04
Also ... Clonezilla does not have the feature of being able to mount a backup image file -- as do the Windows backup apps.

---

### Post by Luc_Lacombe on 2013-11-04
[I][B]Hello Mark Phelps

I burned a CD with _Redobackup_ and it did the job perfectly.
I tried a backup/restore job on a portable with Ubuntu.
I tried the same thing on another one with W$ XP.
And finally on a XP/Ubuntu DualBoot desktop with again, backup and restore.
100% success on these four canidates and tested.

Sorry to learn that backup image mounting is not possible in Ubuntu.
Most of the time this feature can be useful and above all, time saving.
Thanks for the useful cue and thanks also to Leclerc65 and speartip for suggestions.
[/B][/I]
[I][B]Luc Lacombe
[/B][/I]

---

