---
title: "Move Dropbox from ext4 to NTFS partition?"
date: 2013-04-01
forum: General Help
---

### Post by x-shaney-x on 2013-04-01
I'm wanting to move my Dropbox folder from my home folder to my NTFS data partition, preferably without having to re-sync everything.
I tried using the move folder option in Dropbox preferences but I get an error that it cannot move all the files (in fact, it doesn't move any of them).

I am assuming it is a permissions problem but is there any way to do it?

I'm using 12.04 with Dropbox install via the nautilus-dropbox package.

---

### Post by dcstar on 2013-04-02
Non-Linux filesystems cannot be used in many cases because they do not support all the required Linux features.

NTFS is an old Windows filesystem, it is not a Linux filesystem.

---

### Post by x-shaney-x on 2013-04-02
Well yes but I use NTFS for the data partition because it is shared between Windows and Linux installations.
I would rather have a single dropbox that can also be shared between installs too.  I don't see the point of having many GB of photos filling up two different partitions.

Aside from that, I recently uploaded several GB of new photos and as well as taking about 3 days to upload, I then had to wait several hours for them to download again in Windows.

---

### Post by ManamiVixen on 2013-04-02
NTFS Partitions are not well supported, if at all in Linux. If the NTFS partition is nothing but storage space, format it to Fat32 which is supported by Linux and Windows.

---

### Post by fantab on 2013-04-02
> **x-shaney-x said:**
> I'm wanting to move my Dropbox folder from my home folder to my NTFS data partition, preferably without having to re-sync everything.
I tried using the move folder option in Dropbox preferences but I get an error that it cannot move all the files (in fact, it doesn't move any of them).

I am assuming it is a permissions problem but is there any way to do it?

I'm using 12.04 with Dropbox install via the nautilus-dropbox package.

Since we can Read and Write to NTFS from Linux, it is possible (theoritically) to have shared/common Dropbox folder on NTFS that can be updated from both Windows and Ubuntu/Linux.

In /home hit CTRL+H to reveal Hidden dot folders... locate .dropbox and delete it. Open Dropbox and the install Wizard will run asking you to create a dropbox folder, Choose ADVANCE SETUP. Try changing the folder location to NTFS. If in case you are unable to do so, hit Ctrl+L while you have a blinking cursor in the path box. This will open the file manager and you can manually choose the path to partition and folder. Remember this NTFS partition has to mounted for Dropbox from Ubuntu to sync.

If you already have Dropbox folder from Windows in the NTFS partition just choose it.

Let us know if this worked...
Good Luck.

---

### Post by vanadium on 2013-04-02
I would be surprised if it would not work with a much simpler way: a symlink. Replace your Dropbox folder where your synchronized files are with a symlink to the ntfs folder where you want the data.

Stepwise:
1) Move your dropbox folder to the desired location on the ntfs partition
2) Open a second file manager window, in the folder where the dropbox folder originally was.
3) Press Ctrl+Shift and drag the moved dropbox folder to that second file manager. Release the mouse button: a symlink will now be created. The dropbox client will now look into the symlink and through it, see you data on the other partition.

---

### Post by x-shaney-x on 2013-04-02
@ [COLOR=#000000]ManamiVixen
[/COLOR]
I actually switched from fat32 to NTFS for my data partition a couple of years ago for a very specific reason (though I can't actually remember what that is now) and in that time I have not had a single issue using NTFS.

@ fantab

Funnily enough, I tried exactly that earlier today and have spent most of today testing it by copying and removing various files between windows and linux and android.
Everything works perfectly.

This also has the added bonus that when I do fresh installs (such as the upcoming 13.04) I just point it to the new location during install and no need for copying masses of files or waiting for them all to sync after install.

@ vanadium

Tried the symlink method and yes, that also works perfectly.

Thanks all.

---

### Post by Henque19 on 2013-06-27
Hi

I have the same problem, but a symlink didn't fix it unfortunately.
Dropbox starts but seems to hang and shows "92 files downloading.." for hours, without finishing. After a while its CPU-usage goes through the roof so I have to kill it.

My fstab settings are: nfts-3g defaults,auto,uid=1000,gid=1000,nodev,locale=en_US.UTF-8,umask=002 0 0

Any idea what I can do to fix it?

Thanks
/Henrik

---

### Post by CaptainMark on 2013-06-27
You should quit the dropbox daemon so your not syncing, then move your dropbox folder and create the symlink then finally startup the dropbox daemon again.
Otherwise it starts deleting and syncing files at the same time as you're moving them around and can all get a bit messy and possibly resulting in lost data

---

### Post by Henque19 on 2013-06-28
> **CaptainMark said:**
> You should quit the dropbox daemon so your not syncing, then move your dropbox folder and create the symlink then finally startup the dropbox daemon again.
Otherwise it starts deleting and syncing files at the same time as you're moving them around and can all get a bit messy and possibly resulting in lost data

Thanks for the reply. I deleted the symlink and the files in ~/.dropbox to remove all settings and start over. Then I reconfigured Dropbox and when it started downloading files I stopped the daemon ("dropbox stop" right?), deleted the new files, created a symlink to the ntfs partition and started the daemon.

After indexing, it is stuck at "Downloading 89 files...". That is strange since the very same folder is synced in Windows

Is there any way of knowing what files it is trying to download?

---

### Post by CaptainMark on 2013-06-30
Not that I'm aware of which is quite annoying. Sometimes the Dropbox daemon gets very confused and does some weird things, if you can figure out which files are stuck syncing (which hopefully you can do using the syncing icons that should appear over the folders when using the file browser) then try this

1. Move the files out of your synced folders
2. Go to the Dropbox website and delete the problem files
3. Wait for the system tray icon to realise theres nothing left to sync (you might have to quit and restart dropbox for this)
4. Move the files back to their place and let Dropbox re-upload them

EDIT: I also notice you say you deleted the symlinks in the Dropbox folder and reconfigured Dropbox. From previous experience with Dropbox using symlinks I can say you'll get much more predictable results if you store the actual files and folders you want to sync inside your Dropbox folder itself and place symlinks outside pointing in rather than the other way around. For example when I used Dropbox I used to sync my whole photo collection so I created the directory ~/Dropbox/Pictures and put all of my photos in there, then placed the symlink "~/Pictures -> ~/Dropbox/Pictures" I think its something to do with the way Dropbox checks for a directories last modification date, it actually accidently gets the links last modification date and screws up what to sync and what to delete

---

### Post by Henque19 on 2013-06-30
> **CaptainMark said:**
> Not that I'm aware of which is quite annoying. Sometimes the Dropbox daemon gets very confused and does some weird things, if you can figure out which files are stuck syncing (which hopefully you can do using the syncing icons that should appear over the folders when using the file browser) then try this

1. Move the files out of your synced folders
2. Go to the Dropbox website and delete the problem files
3. Wait for the system tray icon to realise theres nothing left to sync (you might have to quit and restart dropbox for this)
4. Move the files back to their place and let Dropbox re-upload them

EDIT: I also notice you say you deleted the symlinks in the Dropbox folder and reconfigured Dropbox. From previous experience with Dropbox using symlinks I can say you'll get much more predictable results if you store the actual files and folders you want to sync inside your Dropbox folder itself and place symlinks outside pointing in rather than the other way around. For example when I used Dropbox I used to sync my whole photo collection so I created the directory ~/Dropbox/Pictures and put all of my photos in there, then placed the symlink "~/Pictures -> ~/Dropbox/Pictures" I think its something to do with the way Dropbox checks for a directories last modification date, it actually accidently gets the links last modification date and screws up what to sync and what to delete

I roughly followed the steps provided by Vanadium to make it work on ntfs that called for symlinking the way I did.

Some progress;I noticed that each time I rebooted, or even restarted the DB daemon, the number of files it was downloading would decrease by one. So I made a simple script that would restart the daemon, wait until it was done indexing then restart daemon again. This repeated until the number reached zero, then it says "Up to date".

But each time a file is added on another computer, the same thing happens. I need to restart the DB daemon as many times as the number of files uploaded. Very strange...

---

### Post by klothius on 2013-07-03
Hi Henque.

I had the exact same problem on archlinux and I solved it by adding default_permissions in mount options in fstab.

It seems that in default mount options for ntfs-3g, default_permissions is not included(although it says **default**_permissions) and is thus causing dropbox(maybe some other apps as well, but this is a first one for me to have issues with writting to a ntfs partition) to loop with downloading. 

It also seems that default_permissions cannot be used validly with 'defaults' as a mount option - I haven't tried it, but a fellow at archlinux forums said he couldn't do it.


[FONT=sans-serif]```

/dev/sdc1       /mnt/DropboxPart          ntfs-3g         rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096  0 0

```

That is the complete entry for my dropbox ntfs partition in fstab. All mount options except default_permissions are by default present when mounting with 'defaults', but as I said earlier, it seems that all options must be explicitly declared if you want to include 'default_permissions'. 

[/FONT][https://bbs.archlinux.org/viewtopic.php?id=165892](https://bbs.archlinux.org/viewtopic.php?id=165892) - this is the link to my thread on archlinux forums.

---

### Post by Henque19 on 2013-07-04
Worked like a charm. Thanks a million!

---

### Post by R33D3M33R on 2013-08-21
Worked for me too, thanks!

---

### Post by R33D3M33R on 2013-09-14
Well, it solved the problem with Dropbox, but now Steam doesn't work at all:

```
Couldn't set up the Steam Runtime. Are you running low on disk space?
Continuing...
```

After adding fixes for steam in fstab, Dropbox stops working. So I'm back at start :(

---

### Post by klothius2 on 2013-09-19
It's probably because in my example I'm setting group id and user id to 0 and you should set it to something else...try it with 1000 for user id or else find out the correct one for your user name...as for the group id, I'm not sure what steam needs - does it need some special group permission or what...

---

### Post by timshel862 on 2013-10-19
I had the same problem as you describe here, but to retain ownership of the partition I put this code instead on fstab, and it worked too.
```
UUID=*****  /media/DropboxPartition  ntfs  defaults,uid=1000,gid=1000,dmask=027,fmask=137  0 0
```

However, it didn't work if I set up user_id=1000, group_id=1000 with the other defaults_permissions sentence as klothius2 indicated, and would only work with user_id=0, group_id=0.

---

