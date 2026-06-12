---
title: "External drive: Files appear in Windows but not Ubuntu"
date: 2013-12-28
forum: General Help
---

### Post by Advait on 2013-12-28
Hi All, 

I installed Xubuntu 12.04 on a friend's pc. He has all his music and movie files on an external NTFS drive. He successfully copied files from an external Apple formatted drive to his external drive. He was not able to copy files from his drive to the Apple drive. Both drives were connected to his Xubuntu pc. His NTFS drive now has the usual ".Trash-1000" directory which I think is something to do with Apple.

He was then having some problems playing some of the files on his external drive while connected to his Xubuntu pc. So I plugged his drive into my Ubuntu 12.04 pc. All the directories on his drive were there but they were all empty. No files and no subdirectories (I tried both in the usual File Manager and in Nautilus; same result). So I then plugged his external drive into my old spare Win Vista pc. All the directories, subdirectories and files were there and I could play them fine (movie and music files).

Strange!

I googled for this problem and didn't get any useful links. I then searched the ubuntuforums and didn't see anything relevant.

Any ideas on what the problem could be? Any important info I forgot to mention? Thanks!

Advait

---

### Post by coffeecat on 2013-12-28
> **Advait said:**
> His NTFS drive now has the usual ".Trash-1000" directory which I think is something to do with Apple.

A .Trash-1000 folder would be what Xubuntu would have written to the drive after he had deleted something. MacOS creates a .Trashes folder, if I remember correctly. 

Since you are able to see folders and files in Vista but not in Ubuntu, I wonder if there is a minor filesystem corruption that Vista can cope with, but not Ubuntu. It might be worth running a chkdsk from Vista on the drive, or the GUI equivalent. For a GUI method in Vista, this would seem to be the one:

[http://windows.microsoft.com/en-gb/windows-vista/check-your-hard-disk-for-errors](http://windows.microsoft.com/en-gb/windows-vista/check-your-hard-disk-for-errors)

---

### Post by Advait on 2013-12-28
OK, thanks! Your reply reminded me of SpinRite so I'm now running SpinRite level 2 on the drive and will post the results. I'll also try CHKDSK to see what that finds. Cheers,

Advait

---

### Post by Advait on 2013-12-29
OK, I ran SpinRite Level 2 on the external NTFS drive and it didn't find any corrupted sectors. Then plugged the drive into my Ubuntu 12.04 and all the subdirectories and files are showing up as normal. Nice! SpinRite performed its usual magic! But then Ubuntu popped up a message saying there's a problem with the drive. The Disk Utility says "SMART Status: Disk failure is imminent." I googled this and found some relevant links:
[URL="http://askubuntu.com/questions/165174/smart-status-disk-failure-is-imminent"]
http://askubuntu.com/questions/165174/smart-status-disk-failure-is-imminent[/URL] and 

[http://askubuntu.com/questions/159368/what-should-i-do-when-hard-disk-failure-is-imminent/159390#159390](http://askubuntu.com/questions/159368/what-should-i-do-when-hard-disk-failure-is-imminent/159390#159390)

So SpinRite apparently fixed the surface problem with the file system, but apparently there's a deeper hardware problem. So now I'll tell my friend to immediately purchase a backup drive and do a full backup. So looks like this thread is resolved.

Thank you coffeecat for your reply! Cheers,

Advait

---

### Post by coffeecat on 2013-12-30
A replacement drive is certainly a good idea! Let's hope your friend can backup the data in time.

By the way, from your first post:

> He successfully copied files from an external Apple formatted drive to his external drive. He was not able to copy files from his drive to the Apple drive. Both drives were connected to his Xubuntu pc. 

His Apple drive would be formatted with the journalled version of HFS+ which is mounted read-only in Ubuntu and variants. But at least it sounds as though his files are still readable on the Apple drive if the NTFS fails one too soon to be backed up. Good luck!

---

### Post by Advait on 2013-12-30
Actually only a small number of his files are on the Apple drive (which belongs to someone else). I don't I was successful in convincing him about the importance of backups. I think he'll need to find out the hard way. Oh well... I warned him.

Thanks for you help! Cheers,

Advait

---

