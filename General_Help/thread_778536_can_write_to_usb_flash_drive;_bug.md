---
title: "can write to usb flash drive; bug???"
date: 2008-05-02
forum: General Help
---

### Post by zedfrugnug on 2008-05-02
Since feisty I've bin having problems with writing permissions to external (FAT32) usb-drives, and system lockups, before this, I used XP.
I don't know if these problems are related. I use the system at my work.

The system freezes generally happen a few times a week, or less. All I can do is reboot..
The system lockups happen mostly when I'm browsing with opera, but since I use the system mostly for browsing, this might be a coincidence.
Also lockups have happened when I wasn't browsing.
I've tested the memory, with memtest, for a full day without errors.
Also I made clean installs of gutsy and hardy.

While using feisty and gutsy, I had a external Western Digital HDD.(FAT32 250 Gb) I found that I should not have the drive connected while installing ubuntu; this would give permissions problems.
Still ocassionally ubuntu would tell me I did not have write permissions..
I always have my usb-drives connected when starting up the system.

Wright now  I'm using a flash usb drive; the corsair flash voyager 8Gb. (also FAT32)
I use it to store my music and and put my thunderbird profile on it so I can use the same profile and mail on another computer (with vista installed) at home. 
Sometimes on start-up thunderbird tells me, it can't write to my flash drive because it is full, or I don't have the wright permissions.
The flash drive is filt to about 60%. 
Rebooting solves the problem most of the times (it's not working now though..)
Properties of corsair tell me, my user can create and delete files and root cannot.
Trying to make a test-file and as root and my user fails both;
tom@tom-desktop:~$ sudo touch /media/CORSAIR/testfile
touch: cannot touch `/media/CORSAIR/testfile': Read-only file system
tom@tom-desktop:~$ touch /media/CORSAIR/testfile
touch: cannot touch `/media/CORSAIR/testfile': Read-only file system

Trying to unmount the volume I am told;
"**do you want to empty the trash, before you unmount?**
In order to regain the free space on this volume the trash must be emptied.
All trashed items on this volume will be permanentely lost"

I choose to empty trash, but when when checking the trashbin, it's still there. Trying to empty the files in the bin manually tells me I cannot, because it's "read-only file system"

I reboot to xp, and delete folder .trash-1000 manually, it's only a few Kb. Reboot again to ubuntu.Trying again to make a testfile, again fails;
tom@tom-desktop:~$ touch /media/CORSAIR/testfile
touch: cannot touch `/media/CORSAIR/testfile': Read-only file system
tom@tom-desktop:~$ sudo touch /media/CORSAIR/testfile
[sudo] password for tom: 
touch: cannot touch `/media/CORSAIR/testfile': Read-only file system

The problem does not seem to be the same as discribed in the thread below, because properties of corsair tell me I do have write permissions. In the thread below the person does not.
[http://ubuntuforums.org/showthread.php?t=770498&highlight=write+external+hd](http://ubuntuforums.org/showthread.php?t=770498&highlight=write+external+hd)


Can anyone help, please??
Is this a bug, or are there still options I haven't tried..

---

### Post by zedfrugnug on 2008-05-19
Bump.

Writing to my usb-drive is again possible without any changes made.
Something was really wrong though;
Afther failing to write in hardy and using the drive with vista on my other system, vista would ask me to scan it for corrupted files, and would find and repair some files. Hardy was messing up my USB-drive..

Altough everything is working properly again, I'm not to happy with the prospect of this possible happening again, and not being able to do anything about it:(

Anyone,, Please?

---

