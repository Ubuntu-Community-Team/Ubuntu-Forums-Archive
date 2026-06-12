---
title: "Ubuntu 18.04.4 - how to properly undelete files"
date: 2021-01-27
forum: General Help
---

### Post by rory4ever on 2021-01-27
Hello,

Today I made a big mistake. I was gonna delete a bunch of redundant files from a subfolder in my home folder. I selected the files and hit shift+del... 1 sec after that moment I realised that I selected the files which I didn't want to delete instead!
My second mistake is that I used Testdisk to try to undelete my files. It found the 3 files I needed but the filesize was 0 so it was of no use but I made some read/write actions on that partition and that is not helping my chances to recover. 
It were 3 text files with important info (yes I know, why not create a backup?) 
I didn't reboot my system since then and there are a lot of ways to recover, so it seems.. but I cannot seem to handle it properly. What are my best options to undelete those files? In fact I even don't need to recover these files, as long as I can look into them. 
Thanks.

---

### Post by HermanAB on 2021-01-28
Maybe you need to read this:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by rory4ever on 2021-01-28
Thanks for the info. It is not helping me at the moment though. I know I need to make backups but right now I only need to retrieve some text files I accidentally deleted.

---

### Post by HermanAB on 2021-01-28
Well, testdisk is what you need to use.  Your mileage may vary, depending on what you did with the system since deleting the files.  Unfortunately, Linux is very good at deleting things...

---

### Post by ActionParsnip on 2021-01-28
Use your backups. Dead dimple. You do make backups......right?

---

### Post by rory4ever on 2021-01-28
> **HermanAB said:**
> Well, testdisk is what you need to use.  Your mileage may vary, depending on what you did with the system since deleting the files.  Unfortunately, Linux is very good at deleting things...

I used that immediately and saw my files (colored in red) but the size of the files were all 0 bytes...

---

### Post by rory4ever on 2021-01-28
> **ActionParsnip said:**
> Use your backups. Dead dimple. You do make backups......right?

I did, but unfortunately I forgot to backup these 3 files. I know, it's stupid and yes I need to learn from that but I hope there's still something possible.

---

### Post by rory4ever on 2021-01-28
Also, if I make use of a paid service of a data recovery company, will it increase my chances? Because I experimented myself with several undelete tools but yeah, it writes data on the disk I lost my files on so that will complicate things. 
If someone knows about a good experience with a paid service, I am happy to know.

---

### Post by TheFu on 2021-01-28
Paid recovery services aren't cheap.  A friend does this stuff for a living.  $3000 per disk last time I heard.  Linux file systems work different from Windows.  Every time you said File--> Save, it is very possible another copy of the nearly same file was written to disk.  So you might find 50 versions of the same file, if you are lucky.  testdisk means scanning the entire partition and recovering all the files of a specific type. This will probably require hours. And you need another disk/storage to receive those files.  Even after all of that, every write to that disk done since the deletion has been putting the data at risk.

In short, make daily, automatic, versioned, backups.  Have a local and remote copy for the stuff you cannot lose.  If you are willing to lose stuff, do the backups less frequently or don't make them automatic.
For end-user files, something like Back-In-Time is fine.  The default settings are in a GUI.  It makes what it calls "snapshots", but they aren't really snapshots.  The target storage needs to be a Linux native file system. It makes snapshots every hour, then selectively deletes them over time.  The snapshots use hardlinks between versions, so you don't end up with 40 copies of a file if you have 40 snapshots.  Hardlinking is a time honored backup method for Unix systems that's been used 30+ yrs.  B-i-T has a shell version and a GUI.  My 80+ yr old mom used B-i-T for years.

All this talk of backups sounds harder than it needs to be, unless you have difficult demands.  Backing up everything in your HOME is pretty easy.  Backing up most things in your HOME, but not bothering with .cache/ .trash/ and any temporary files becomes a little more complex.  

Backing up files that are open is much harder, unless you don't worry about corruption of those files.  Unix/Linux doesn't have automatic "shadow copies" like Windows does, but it does have techniques which do much better than simple shadow copies thanks to the different volume management tools.  Alas, those tools must be setup in advance, before any file system is created. For most users, that means during installation.

---

