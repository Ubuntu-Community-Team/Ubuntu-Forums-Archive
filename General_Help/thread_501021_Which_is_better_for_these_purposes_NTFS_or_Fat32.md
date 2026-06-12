---
title: "Which is better for these purposes? NTFS or Fat32?"
date: 2007-07-14
forum: General Help
---

### Post by HighD on 2007-07-14
Ok, I will explain my problem ( I've seen other similar threads but I just can't decide on what to do) :confused:

Let's start with my current hd setup:


44 GB - Windows XP | NTFS ( C: )
20 GB - Linux | Ext3 (/)
1GB - SWAP
85GB - Documents, Videos, Software | NTFS ( E: )
***_85GB - Music | FAT32 ( F: )_***

As you can see, I Dual-Boot, so at first I decided to go with at least one FAT32 partition ( in this case F: ) so I could share between both OS.

Recently, I have discovered ntfs-3g, which I've tested on E: and seems to work very well. This led me to think, why do I need FAT32? I can now just write to NTFS as well!

I've also read that formatting partitions bigger than 4GB on FAT32 is a bad idea, I know it can't handle large single files very well, but I don't use for that purpose, still that bugged me.

Now correct me on this : I've ALWAYS believed NTFS is better than FAT32, more secure, not in terms of encryption or data security, but in terms that it won't fail on me as I use my partitions A LOT: write, erase and re-write, as well as admitting more characters on file paths, that is my main concern. 

On my FAT32 drive, I store mainly mp3,m4a,flac,mpc..and so on... files, my whole music collection, so it is VERY IMPORTANT to me. So now that I can use ntfs-3g, is it wise to go from fat32 to ntfs? Is FAT32 a safe filesystem to store my music collection?

Well thanks so much in advance for all your help :mrgreen: Ubuntu community is great!

---

### Post by davidjmayo on 2007-07-14
Hate to say this on an ubuntu forum but I'm going to do it the windows way..

FAT32 is safe but old. NTFS is better

 if you want to:
If you are happy with ntfs you can use your windows to convert the FAT32 to NTFS

Boot into windows not ubuntu
Open my computer. Right click on the drive F (in your case)  and then properties. look in the tabs, one  tab should say something like  convert the file system to NTFS (sorry not very helpful but a long time since I did this)


If not you need to run it from a command line 

Start==> run==>  then type **command **(i think but dont remember)

The command (and again check by help convert  or convert /? ) I think is
convert [drive letter:]  fs\ntfs                 CHECK THE COMMAND IN WINDOWS BEFORE YOU DO THIS as I dont remember the correct command (been a long time since I did it)

You need to reboot windows and it will handle the conversion to ntfs, just wait for it to run through

---

### Post by dasunst3r on 2007-07-14
As far as creating a partition to share files between Windows and Linux is concerned, I prefer NTFS because FAT32 is simply old and busted.  For write access, use ntfs-3g.

---

### Post by smoker on 2007-07-14
hi, to me, not being an expert in the pros and cons of specific file systems, if it is working for you, why change?

saying this, you wont know if ntfs is better until you try it, but remember there is always a risk changing file systems containing data, so if you follow david's good advice above, have a good backup of all your crucial data.

also, run your defrag in windows a few times to tidy up your fat32  drive before conversion, get all the 'bits n' pieces' together!

best of luck

---

### Post by merlinus on 2007-07-14
My ubuntu way is to format everything except my windows partition (which is ntfs) to ext3, and use the ifs driver to access and write from windows to them.

And I use ntfs-3g for writing from ubuntu to windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

-merlin

---

### Post by HighD on 2007-07-14
> **smoker said:**
> hi, to me, not being an expert in the pros and cons of specific file systems, if it is working for you, why change?

Good question...I just want to move forward... as dasunst3r says : 

> **dasunst3r said:**
>  I prefer NTFS because FAT32 is simply old and busted.

I guess I'll follow smoker's advice, backup my stuff first and then do the conversion, or just reformat.

Thanks everyone :D

EDIT: Ok DONE! :D, what I did was move my music to another drive and reformatted to NTFS. Everything went ok :D. Now I'll just be happy reading and writing with ntfs-3g. Thanks again everybody :mrgreen:

---

