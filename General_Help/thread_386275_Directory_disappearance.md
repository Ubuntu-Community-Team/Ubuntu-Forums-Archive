---
title: "Directory disappearance"
date: 2007-03-16
forum: General Help
---

### Post by Emceay on 2007-03-16
I installed edgy and it was working flawlessly. I had my music stored in one folder on a separate hard drive in ex3. SongBird was playing music from the folder when suddenly one day it just vanished. It wasn't deleted, there's nothing in the trash. Running a search doesn't find the folder "My Music". It's not hidden, and I can create a new directory with the same name.
Linux didn't really just devour my music collection right? There's some way to recover it isn't there? Can anyone point me in the right direction?

---

### Post by Dr. Nick on 2007-03-17
can you see anything else on the separate drive? Maybe its not mounted anymore

---

### Post by Emceay on 2007-03-17
That's the most peculiar thing, everything else is still on the drive. I've just lost my music folder and all of my albums in it.

---

### Post by Emceay on 2007-03-18
-Bump-

This certainly doesn't seem common, but has anyone experienced anything like this before?
A single folder on my drive has vanished without record. Everything else is untouched.

Any help is much appreciated.

---

### Post by Kateikyoushi on 2007-03-18
If songbird was using that directory I would look around songbird first, bugd forum also check your logs in /var/log maybe can find something related yo your problem.

---

### Post by peabody on 2007-03-18
Was your computer improperly powered off recently and did a file system check take place?

---

### Post by Emceay on 2007-03-18
Yes, and yes. Songbird froze and no buttons were accessible, so after a forced reset fsck was run.

---

### Post by peabody on 2007-03-18
I'd check the lost+found folder of that partition.

---

### Post by Emceay on 2007-03-18
Okay, in the Lost + Found folder, I found a ton of folders and music files. I think it's them, but they're all named stuff like #1525897
Any idea how I can get them to go back to my music folder?

---

### Post by peabody on 2007-03-18
Sadly I don't have a good recommendation other than copying or moving them and renaming them manually.  Part of the reason they ended up in the lost+found in the first place was that the metadata in the filesystem went foobar.  If someone else has any recommendations, I'm all ears as I would love to know as well.

I've heard that cowbell music organizer does a good job with ID3 tags, but I'm not sure about filenames.

---

### Post by Emceay on 2007-03-18
Well, at least it's good to know they're still intact. Linux sure is weird, but I still love it.

*86s SongBird*

---

### Post by Dr. Nick on 2007-03-18
If the id3 tags are still good you can check into easytag aswell, should be able to rename the files from tags.

Glad you found them.

---

### Post by Emceay on 2007-03-18
I'm still having a problem though.. Now that I can see some of them (I found that a vast amount are trashed) I can't move them from the lost+found folder.

I've tried chown -R on the whole drive, and just the lost+found, but i get a result that says "chown: changing ownership of `file' : read-only file system" after each operation. I've tried chmod 777 but that has the same result.

How can i gain permission to the lost+found folder? At the moment, I can't even delete junk files.

---

### Post by llamakc on 2007-03-18
Use "sudo"

---

### Post by Emceay on 2007-03-18
Was. That's the result I get.

---

### Post by llamakc on 2007-03-18
Have you ran an fsck on the partition yet?

---

### Post by Emceay on 2007-03-18
Yes. I had it fix errors, now I'm trying to recover what's left.

---

### Post by Emceay on 2007-03-18
> :~$ sudo chown mark:mark /media/data/
chown: changing ownership of `/media/data/': Read-only file system

If I add -R to make it recursive, all results have that "Read-only file system" attached to the end. When I click properties, the folder and all it's files still belong to root. If I try to change it through properties, it tells me:

> Couldn't change the owner of "data" because it is on a read-only disk.

So.. I'm unable to copy or rename files without permissions. My files are locked in the lost+found folder. Anyone know how to solve this?

---

### Post by llamakc on 2007-03-18
What about remounting it with rw?

sudo mount -o remount,rw /dev/partition /path/to/mount

---

### Post by peabody on 2007-03-18
> **Emceay said:**
> I'm still having a problem though.. Now that I can see some of them (I found that a vast amount are trashed) I can't move them from the lost+found folder.

I've tried chown -R on the whole drive, and just the lost+found...

YARGH!!  I'm assuming this drive is an external or some such?  If that's the case, then that's...survivable, but don't EVER do that to something like your root partition!  That can mean a reinstall!

I know you seem to blame SongBird for this, but I don't think it had anything to do with this.  Emceay, I think you're faced with hardware failure.  Linux remounts partitions read-only when they have I/O errors.  Back that drive up pronto.

Might not be the case, but you can never be too careful.  If writing to this drive was no problem before, my guess is that's exactly what's happened.  dmesg might be enlightening in this case.

---

### Post by Emceay on 2007-03-18
Hrm.. it wants a filesystem type.. I'm not sure where to specify it.
How do I backup the stuff on it if it won't let me copy files from it?

---

### Post by peabody on 2007-03-18
EDIT: frankly, I wouldn't dare remount rw until you've verified that the drive is stable.

It won't even let you copy?  How are you trying to copy the files?  Is there anything in your /var/log/messages that talks about I/O errors? What is the output of the "mount" command without any arguments?

---

### Post by Emceay on 2007-03-18
this is what sudo mount returns:
> /dev/hdb1 on /media/data type ext3 (rw)

this is one of many like it in my log.
> Mar 18 20:04:04 Darklight kernel: [17253900.348000] end_request: I/O error, dev hdb, sector 49603503

It still claims it's read-only when I try to move files off the drive or create new folders within it.

---

### Post by peabody on 2007-03-18
Your drive is failing, do you have any other media to work with?  You won't be able to copy the files to the same drive.

---

### Post by Emceay on 2007-03-18
Yeah, I have two other drives attached to the same computer. I have the root-nautilus-here script and usually it lets me write between drives.. not today. Is there anyway I can unlock this drive one last time to save what I can before it gets reformatted?

---

### Post by peabody on 2007-03-18
> **Emceay said:**
> Yeah, I have two other drives attached to the same computer. I have the root-nautilus-here script and usually it lets me write between drives.. not today. Is there anyway I can unlock this drive one last time to save what I can before it gets reformatted?

Reformatted?  That drive is physically toast.  I wouldn't trust it as far as I could throw it.  So, when you try and use something like "cp file /path/to/folder/on/some/other/drive" it doesn't let you copy?

Edit: if you have the space are you able to do something like "tar cvf tar_backup.tar /path/to/read/only/filesystem/thats/failing" from within a folder on a drive you can write to?

---

### Post by Emceay on 2007-03-18
Well.. now i notice that I can copy the data outside of the music folder to a new drive.. But in terminal it says access denied when I try to cd lost+found... :\
That's... not normal is it?

---

### Post by peabody on 2007-03-18
> **Emceay said:**
> Well.. now i notice that I can copy the data outside of the music folder to a new drive.. But in terminal it says access denied when I try to cd lost+found... :\
That's... not normal is it?

If the folders don't have execute permission it's normal.  Never heard of it being a problem before, but could be that the read only mounting is denying execute permissions as well.

Edit: So, since you can get data from the drive, I'd use tar to backup.

---

### Post by kvonb on 2007-03-19
Here's an idea:

Boot from the Ubuntu CD, then run a terminal and mount your drives like so:

```
sudo mkdir /mnt/hda1
sudo mkdir /mnt/hdb1
sudo mount /dev/hda1 /mnt/hda1
sudo mount /dev/hdb1 /mnt/hdb1
```Of course I'm guessing as to the hda1, you need to find out which is which by typing:

```
sudo fdisk -l
```Then run a root Nautilus, press <ALT><F2> and type this in the box:

```
gksu nautilus
```Both drives should now be completely read/write to you, so using Nautilus, copy as much as you can onto your good drive (hda1).

If you are limited for space on your good drive, you could copy 700 megs worth, then burn it to CD, (you can install Gnomebaker through synaptic while using the LiveCD :) ).

And PLEASE take **peabody**'s advice, take a hammer to that drive once you have taken all your files off it, it **WILL** give you grief in the very near future, that I can guarantee!  Even if it re-formats as good.

Actually, if you look on the manufacturers web-site you should find an RMA section where you can check the drive's serial number to see if it still under manufacturers warranty.  You might get a free replacement sans the cost of postage :).

---

