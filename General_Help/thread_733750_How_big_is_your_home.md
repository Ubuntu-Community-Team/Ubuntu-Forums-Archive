---
title: "How big is your /home?"
date: 2008-03-24
forum: General Help
---

### Post by Kiri on 2008-03-24
I'm wondering how big most people's /home partition or folder is after running ubuntu for a length of time (at least a few months) MINUS data such as downloads, music, video, photos , etc?

The reason I ask is this:
I want to install ubuntu with a separate /home partition so that I can ugrade/re-install and retain all my settings and configuration (hopefully, if I understand the theory correctly). 

But I am planning to keep most of my 'data' (music, docs, videos, downloads,  etc, etc) on a separate shard NTFS partition shared with ubuntu and windows. 

So with that setup in mind, how big do you think my /home partition for ubuntu should be given that I will not be storing much apart from the settings etc in there. 
(I might try and setup links to my other disk to work from the home folders though... )


I want to keep it fairly small since I only have about 30gb free, and I want as much as possible for my shared partition. 

Thanks!
:KS

---

### Post by codeslicer on 2008-03-24
Upgrading Ubuntu doesn't delete all your settings, unless you reformat the hard drive and start from scratch. If you use the Update Manager, it should work just like if you were upgrading a package - sometimes your configuration gets overridden, sometimes not. I upgraded to Hardy several days ago and so far it looks like I didn't lose anything....

When you install Ubuntu, you can always mount that shared partition on your home directory - mount it on /home/yourusername. Of course if you don't want all those config files that show in Windows Explorer, then you should still use a separate partition.

For me, my home folder, excluding downloads, docs etc, is about a gig, but that can't be too accurate because I have installed wine and later tons of frameworks, so excluding that would be like... 60mb!! That's not a lot, as tons of temp files are thrown in to that.

My suggestion: don't create a seperate /home partition, if you do you definately don't need more than a gig.

---

### Post by mali2297 on 2008-03-24
The hidden configuration and settings files shouldn't take much space. Cache files (Firefox), thumbnails and such can take a lot of space though. I would say that you need 100 MB for those, perhaps more. In addition, if you intermediately download files to your home folder, you must take that into account.

Personally, I don't set up a separate home partition. I prefer to backup my configuration files before a clean installation and put them back afterwards. Some of the settings I don't want to restore since they might be obsolete or conflicting with the new system.

---

### Post by TenPlus1 on 2008-03-24
my filesystem partition is 30gb and my /home partition is the remainder (120gb) of the hard-drive...  Works for me :)

---

### Post by Nameless_one on 2008-03-24
My /home partition, minus my own data is 1,56 GBs, but that includes tracker's 900 MB cache and my thumbnails folder which is 400 MBs, so the settings alone are no more than 200 MBs. However, you should probably give 2-3 GBs to your home for thumbnails and such.

---

### Post by Kiri on 2008-03-24
Thanks a lot everyone who replied. It sounds like I can get away with having a fairly small partition of just 1 or 2 GB. Which is good, because I don't have a whole lot of HD space to spare :-k

---

### Post by solitaire on 2008-03-24
i've got a 3Gb /Home partition (only got a 27Gb drive) It does for day to day useage (but i stuff everything big on a 250Gb External USB box that's got symbolic links to the movies, audio folders).

---

### Post by Kiri on 2008-03-24
> **solitaire said:**
> i've got a 3Gb /Home partition (only got a 27Gb drive) It does for day to day useage (but i stuff everything big on a 250Gb External USB box that's got symbolic links to the movies, audio folders).

Do you mean that you have symbolic links going from your external drive to the relevant folders in your /home directory?

I would also like to set something like this up. Could you tell me briefly how you did it? I do not know anything about symlinks yet...

---

### Post by solitaire on 2008-03-24
ln -s -f /original/file/name/path /new/link/path

*Warning*
it's not perfect i usualy have to remake the links to the USB drive every so often if i reboot my laptop.

If you're on a desktop and it's linking to another HDD then this won't be an issue.

---

### Post by Kiri on 2008-03-24
Thanks for the info. I'm also on a laptop. 
One question, is the /original/file/name/path the path to the directory on your external, and /new/link/path to your /home? Or the other way round?

I'm just a bit confused about the direction it is going in... I would have thought that you would make a link from your /home TO the folders where your data is (?)

---

### Post by jken146 on 2008-03-24
The first path is the actual location of the file and the second path is the location of the link (the file that points to the original file).

---

### Post by solitaire on 2008-03-24
The first part is to the USB drive (the location of the stored data)
The Second part is the link to your /home/<username>/Folder/ directory

I use: ```

ln -s -f /media/MyBook/Pics /home/sol/pictures

```

just make sure there are no spaces in any of the folder names (it's a pain to sort out)

---

