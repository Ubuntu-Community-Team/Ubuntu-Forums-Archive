---
title: "Cross Platform Torrent Support"
date: 2007-04-23
forum: General Help
---

### Post by lenordbater on 2007-04-23
I'm in the process of trying to move away form Windows XP and into Ubuntu.  I've found solutions for almost everything I do in Windows except for Photoshop (I know I know, The Gimp is great, but still lacking in a few important areas like RAW support), so for the foreseeable future I'll be frequently dual booting between the two OS's.  

One problem with this situation I haven't been able to overcome is continuing to download the same torrents in both OS's.  I'd like to be able to, for example, be downloading the Feisty Fawn iso in Windows while I'm doing some Photoshop work, then have that torrent automatically pick up where it left off when I log off and boot into Ubuntu.  

I thought the solution might be to run uTorrent in Windows, than run the same program in Ubuntu under Wine.  I got uTorrent to run under Wine, but it seems to use a different settings file than under Windows.  

Is sharing torrents across multiple OS's a hopeless dream, or is there a way I might be able to accomplish this?

---

### Post by Tsen on 2007-04-23
It can be done, but there will be some setup involved.

First of all, you'll need read-write access to your Windows partition (via NTFS-3g or somesuch), ext3 access from your Windows partition, or a separate partition that both can read (FAT32 or something).  You only need one of the above.  A separate partition would probably be easiest, but if you can get NTFS-3g working, then you're set.
Then, in uTorrent (or another torrent program, but uTorrent kicks butt, so we'll use it) go to Options->Preferences->Other, and then change the "Store .torrent files in:" option.  If you have a separate partition, then create a new folder on it called "Downloads" or something, then inside that folder create another called "Torrent Files".  Change the "Store .torrent files" box to point to that folder.
In the same area, change the "Automatically load .torrents in directory:" to point to the same folder as you used in the previous step.
Now go to Options->Preferences->Downloads and change the "Put new downloads in:" box to point to the Downloads folder on your partition.

Change the settings in Linux, too (Or Windows, if you configured Linux first) to be the same as this.  
Walah!  When you open up uTorrent in either OS, it should automatically load all the torrents, find the downloads in the /Downloads folder, verify the file contents, and pick up where you left off.

If you installed NTFS-3g, then change the folder for stored torrents and downloads to be on the Windows partition instead of a separate partition, and if Windows is enabled to read ext3, then change it to be on the Linux partition.

If I didn't explain something well, just ask!

---

### Post by lenordbater on 2007-04-23
Thanks so much!  I'll give it a go right now.  

If I'm understanding correctly I'll have, for example, a folder /Downloads/Torrents/ where all my .torrent files are, and all the actual data being downloaded will be in /Downloads/, correct?

---

### Post by Tsen on 2007-04-23
Yup.  You don't really need to set it up that way--you could, for example, put the .torrents in the same folder as the downloads, but this way keeps things a bit more organized.

---

