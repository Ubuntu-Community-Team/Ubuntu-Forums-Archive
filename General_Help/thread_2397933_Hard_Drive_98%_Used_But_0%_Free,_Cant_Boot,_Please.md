---
title: "Hard Drive 98% Used But 0% Free, Cant Boot, Please Help"
date: 2018-08-05
forum: General Help
---

### Post by typos1 on 2018-08-05
I recently used deluge to download a torrent but forgot to set the location as a USB drive so my hard drive had 0bytes remaining, I deleted the file and used force quit to kill deluge as it was hanging. Unfortunately I pressed the mouse too soon and killed unity which caused the system to crash. Now I can't boot, I get a "couldn't get size" error on a black screen. In recovery the hard drive is showing as "103gb - 98% used, 0% free". I don't think I removed the file from deluge and normally if you delete a file from a hard drive but don't delete it from your torrent client, the free space does not show up, it only shows up when you remove it from the torrent client. So I figured this could be the problem. I removed deluge from root shell prompt, hoping it would free up the missing 5gb but it didn't. I've used clean and fcsk but I can't free up any more space, I did free up 167mb of space by removing un-needed packages but I still don't have any free space. I tried running Nautilus to remove any remaining files from deluge, but it won't run, can't remember what the exact error was but it couldn't run a display server or something, I guess cos of the lack of space ? I've been trying to fix this for days, can anyone help ? Thanks

---

### Post by TheFu on 2018-08-05
Unix file systems are generally setup with a 5% reserved for root tuning parameter.  Only root can access that last 5% of space.  This is smart on /, /var/ and other core OS partitions, but unneeded on /home/ or other disks usually.  You can tune this parameter using **tune2fs**, with certain assumptions.  Don't confuse directories with partitions.   Logical volumes can be considered partitions, in this case.

A best practice is to have separate /var and / file systems, keeping end-user storage elsewhere.  If the system is setup with 1 huge filesystem shared by all, then reducing the reserved space may not be a good idea. The fact that the system is behaving badly shows that perhaps for this specific system more than 5% should be reserved.

It doesn't work for NTFS, FAT-whatever or BTRFS.  BTRFS lies about storage space unless you use their custom tools.

---

### Post by SeijiSensei on 2018-08-05
As TheFu says, you're likely bumping up against the reserved space.

One place to find files that can be deleted is /var/log, especially if you have rotations enabled so that there are logs from prior weeks.  Anything in /var can only be deleted by root.

Next stop is your /home/username directory.  Any stuff you can dump in Downloads?

For a quick overview of space usage run 
```

cd / 
sudo du -h *

```
which will list the main directories off the root with their sizes.

---

### Post by typos1 on 2018-08-05
> **TheFu said:**
> Unix file systems are generally setup with a 5% reserved for root tuning parameter.  Only root can access that last 5% of space.  This is smart on /, /var/ and other core OS partitions, but unneeded on /home/ or other disks usually.  You can tune this parameter using **tune2fs**, with certain assumptions.  Don't confuse directories with partitions.   Logical volumes can be considered partitions, in this case.

A best practice is to have separate /var and / file systems, keeping end-user storage elsewhere.  If the system is setup with 1 huge filesystem shared by all, then reducing the reserved space may not be a good idea. The fact that the system is behaving badly shows that perhaps for this specific system more than 5% should be reserved.

It doesn't work for NTFS, FAT-whatever or BTRFS.  BTRFS lies about storage space unless you use their custom tools.

Thanks for your response.

The system isn't behaving badly, it was deluge and me that behaved badly. 

I'm aware of the root partition and mine is 500mb, I always thought it was for situations like this but clearly it isn't.

The system is set up as the ubuntu installer set it up alI I did was set the swap partition size.

Thanks for all the info but I don't understand how any of it helps, other than the suggestion that I resize the root partition to gain extra space, unless in missing something ? I thought I needed to find the offending deluge files and delete them?

---

### Post by typos1 on 2018-08-05
> **SeijiSensei said:**
> As TheFu says, you're likely bumping up against the reserved space.

One place to find files that can be deleted is /var/log, especially if you have rotations enabled so that there are logs from prior weeks.  Anything in /var can only be deleted by root.

Next stop is your /home/username directory.  Any stuff you can dump in Downloads?

For a quick overview of space usage run 
```

cd / 
sudo du -h *

```
which will list the main directories off the root with their sizes.

Thanks for the reply. 

Yes I realise I m up against reserved space, I m looking for advice on how to delete from command line, I'll try var/log but I use ubuntu tweaks janitor after every update. 

As it's deluge that caused this problem I'll be deleting anything left behind after it was removed which will most probably be the file that caused the problem in the first place.

I ve already reviewed my storage, this is how I found out why wont boot.

I should have purged when I removed deluge then all associated files would have been removed, unfortunately only found this out after I removed deluge.

---

### Post by Yellow Pasque on 2018-08-05
> I don't think I removed the file from deluge and normally if you delete a file from a hard drive but don't delete it from your torrent client, the free space does not show up, it only shows up when you remove it from the torrent client.

That doesn't make sense. If you actually deleted the file (not Trash or Recycle Bin) and the command completed correctly, you should have the space back. If you delete part of a torrent while in action, the client should complain and stop that torrent, and/or maybe try to re-download it.

---

### Post by Yellow Pasque on 2018-08-05
If you're able to get to a command line, then search for files larger than 1GB
[http://www.linuxlookup.com/howto/find_all_large_files_linux_system](http://www.linuxlookup.com/howto/find_all_large_files_linux_system)

Also, you may want to see if Deluge left anything behind in ~/.config
Remember that ~/.config is hidden.

---

### Post by TheFu on 2018-08-05
I hope / (the root partition) is much larger than 500MB.  That's a good size for the /boot/ partition.  Details matter.

---

### Post by typos1 on 2018-08-06
> **Temüjin said:**
> That doesn't make sense. If you actually deleted the file (not Trash or Recycle Bin) and the command completed correctly, you should have the space back. If you delete part of a torrent while in action, the client should complain and stop that torrent, and/or maybe try to re-download it.

That's how deluge and transmission work in my experience - if you delete the file but don't remove it from the torrent client the space is still used, almost as though they has some sort of cache or backup.

---

### Post by typos1 on 2018-08-06
> **TheFu said:**
> I hope / (the root partition) is much larger than 500MB.  That's a good size for the /boot/ partition.  Details matter.

Lol, stupid me getting boot and root partitions confused !

---

### Post by Impavidus on 2018-08-06
A file is gone as soon as you remove it AND no running processes keep the file open. The torrent process keeps the file open, so it's only deleted when the torrent client is closed. But that may already have attempted to recreate the file. If you first close the torrent client, then remove the file, it should be gone. But even then, the torrent client can automatically recreate the big file when it's restarted, unless the .torrent file is removed. So it indeed makes sense that you have to remove the file from the torrent client or it won't be gone for more than a second.

When you boot using a live disk or into recovery mode (don't forget to mount your root or /home partition, if you have any, in read-write mode), the torrent client won't be started, even if it's in your list of startup applications. It seems that's the only way you can boot anyway. Delete the big file and remove the .torrent file from the place where the torrent client expects it.

---

### Post by typos1 on 2018-08-06
> **Impavidus said:**
> A file is gone as soon as you remove it AND no running processes keep the file open. The torrent process keeps the file open, so it's only deleted when the torrent client is closed. But that may already have attempted to recreate the file. If you first close the torrent client, then remove the file, it should be gone. But even then, the torrent client can automatically recreate the big file when it's restarted, unless the .torrent file is removed. So it indeed makes sense that you have to remove the file from the torrent client or it won't be gone for more than a second.

When you boot using a live disk or into recovery mode (don't forget to mount your root or /home partition, if you have any, in read-write mode), the torrent client won't be started, even if it's in your list of startup applications. It seems that's the only way you can boot anyway. Delete the big file and remove the .torrent file from the place where the torrent client expects it.

I removed the torrent client in recovery but I still have the problem. I also deleted the file from my hard drive before I had the problem, so its already not in the place where the torrent expects it.

I ve found 3 deluge files in /home/username/.config and 3 in /var/lib, can anyone talk me through how to delete them safely ? - I'm not experienced with the rm command and afaik it can be very dangerous if you get it wrong, I don't want to accidentally delete loads of my files.

---

### Post by Yellow Pasque on 2018-08-06
If you don't care about saving anything from deluge (like your configuration or misplaced torrents), sending the entire ~/.config/deluge directory to the great bit bucket in the sky is the easiest way.
```
rm -r ~/.config/deluge
```

If you want to selectively search for the large file(s) in question, use the find examples I gave in my previous post on the directories in question (~/.config/deluge and /var/lib/deluge). Maybe this will be informative too: [https://unix.stackexchange.com/questions/34140/tell-fs-to-free-space-from-deleted-files-now](https://unix.stackexchange.com/questions/34140/tell-fs-to-free-space-from-deleted-files-now)

---

### Post by Yellow Pasque on 2018-08-06
> I should have purged when I removed deluge then all associated files would have been removed

Well, you can still run 'apt purge' on a package you ran 'apt remove' on. If there's any .conf files and dirs left behind in /etc, they'll be removed. 
However, 'apt purge' won't remove config files/dirs the program has created in the home directory, so I doubt it will solve your issue or free up a lot of space.

---

### Post by typos1 on 2018-08-06
> **Temüjin said:**
> If you don't care about saving anything from deluge (like your configuration or misplaced torrents), sending the entire ~/.config/deluge directory to the great bit bucket in the sky is the easiest way.
```
rm -r ~/.config/deluge
```

If you want to selectively search for the large file(s) in question, use the find examples I gave in my previous post on the directories in question (~/.config/deluge and /var/lib/deluge). Maybe this will be informative too: [https://unix.stackexchange.com/questions/34140/tell-fs-to-free-space-from-deleted-files-now](https://unix.stackexchange.com/questions/34140/tell-fs-to-free-space-from-deleted-files-now)

Thanks i used the find command then I took the plunge and used rm to remove all deluge files I could find, still wont boot, I ll try this in case I missed any.

---

### Post by typos1 on 2018-08-06
Still no luck. Can anyone tell me the correct command to delete a file from the desktop? I really don't wanna risk deleting everything. Would it be ```
rm /home/username/Desktop/filename
``` ?

---

### Post by Impavidus on 2018-08-06
That's right. Substitute your username. From your location I assume you use english, but if not you also have to change "Desktop" to the local translation, as that directory name is localised.

---

### Post by typos1 on 2018-08-06
Ok, I gave up with that - file names with brackets in the title arent recognised, i get a syntax error. I the end I used my Android phone to create a bootable sdcard. I used that and deleted the offending file - it was still on the desktop, could have sworn I deleted it though.

Anyway, it STILL wouldnt boot and STILL had "0% free", despite having deleted the 2Gb file, no amount of fsck ing would sort it, so I had to delete other stuff.

Now the pc is up and running but I ve "lost" space - before this incident I had 1.5Gb free, now I only have 500mb free, which is strange.

Thanks for everyones help so far, anyone know how to retrieve the lost space ?

---

### Post by HermanAB on 2018-08-07
There seems to be multiple people with disks full of junk, so you are not alone.

You can delete all the files in /var/log.  That would likely free up about 500 MB.  Important log files will be recreated automagically.  Unimportant things will stop logging, which is not bad either.

You can look for large junk files with disk use (du):
# du -a /var | sort -n -r | head -n 10
or
# du -a / | sort -n -r | head -n 10

and delete them.

You can eliminate duplicate files and save another few gigs with the hardlink utility:
$ hardlink -c /home

---

### Post by typos1 on 2018-08-08
> **HermanAB said:**
> There seems to be multiple people with disks full of junk, so you are not alone.

You can delete all the files in /var/log.  That would likely free up about 500 MB.  Important log files will be recreated automagically.  Unimportant things will stop logging, which is not bad either.

You can look for large junk files with disk use (du):
# du -a /var | sort -n -r | head -n 10
or
# du -a / | sort -n -r | head -n 10

and delete them.

You can eliminate duplicate files and save another few gigs with the hardlink utility:
$ hardlink -c /home

Thanks for the suggestion, I ve looked in /var/log and deleting all logs would only free up around 15mb, but /var/log/journal folder is 2.6Gb, is this normal ?

---

