---
title: "FSCK Problem"
date: 2006-12-01
forum: General Help
---

### Post by Declan on 2006-12-01
Hi all,

I'm getting an error on boot. The logged message is this: 

Log of fsck -C -R -A -a
Fri Dec  1 12:45:48 2006

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=c05e935a-e1b7-4ce0-b9da-133ede418ff3'
/dev/hda8: clean, 5486/244320 files, 52538/487966 blocks
/home: clean, 21955/3084480 files, 3758438/6162927 blocks
fsck died with exit status 8

I suppose the cause of this is related to my installation of elive on hda1. It obviously changed the way in which that partition presents itself to ubuntu. Since there is no reason for my using hda1 while in Ubuntu, one approach might be to hide hda1 from fsck (whatever fsck is).
How might I get fsck to skip hda1, or is there a way to get it to "resove" the UUID?
Apologies if the question makes no sense... I don't really understand the question myself. I would however like to be able to boot up smoothly again.

Declan

---

### Post by LLRNR on 2006-12-01
The fsck thing is useful - it's forcing a check of your filesystem every 30th boot (by default)... and if **fsck** simply *dies with exit status whatever* I have the slight feeling that this ain't good.

LLRNR

---

### Post by LLRNR on 2006-12-01
Alright, I have an idea. **fsck** should automatically find all problems on your filesystem and *attempt* to correct them. I think it's best to force a check at your next boot, so use this:
```
sudo tune2fs -c 1 /dev/hda1
``` (**Replace** "hda1" with your root partition)

and then reboot, let fsck do its check.

Hopefully it will be able to repair all the errors encountered. To make it behave normal (i.e. force a check every 30th boot) use the following:
```
sudo tune2fs -c 30 /dev/hda1
``` (again, replace hda1 with your root partition)

LLRNR

---

### Post by Declan on 2006-12-01
OK, I'll try that. The main partition I boot from, however, is hda5 and ubuntu boots fine, just as soon as I CTRL-D its objection to hda1. And the elive installation is fine too. So, I don't think there's anything all that serious going on. But I will force that check, just to see what it says. I dare say I won't understand a word of the output...

Thanks,

Declan

---

### Post by LLRNR on 2006-12-01
How's your /etc/fsbab file ? Paste this in:
```
cat /etc/fstab
```

And then again... don't be so "sure" on your filesystem :D I installed Edgy 3 or 4 days ago (fresh install, I had Dapper before) and, since I'm paranoid, I force a fsck check **every single boot**... Guess what ? In 3-4 days, it found errors 3 times on my filesystem, so... it's best to let fsck do its job, it knows better than me what's going on with my filesystem.

LLRNR

---

### Post by Declan on 2006-12-01
fstab says the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=68cca515-1304-4c1d-b78e-e3c6ae3d62cc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=c05e935a-e1b7-4ce0-b9da-133ede418ff3 /media/hda1     ext3    defaults        0       2
# /dev/hda8
UUID=8027b338-ab7f-47d5-b109-eac2bfa896c8 /media/hda8     ext3    defaults        0       2
# /dev/hda7
UUID=b0ed8c82-3dc7-47a7-b674-96cc68f9c805 /media/storage  ext3    defaults        0       2
# /dev/hda6
UUID=93aaed95-de1f-489c-87d1-5ae5b702fdd6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


How does that look to you? 

Declan

---

### Post by LLRNR on 2006-12-01
It looks alright to me. I see that your /dev/hda5 partition is the one with the / mount point, so in my post above I'll have to correct the "code" lines to this specific case:
```
sudo tune2fs -c 1 /dev/hda5
sudo tune2fs -c 30 /dev/hda5
```

In your fstab file, on each line, the last number represents the fsck options:
0 means disable fsck check;
1 means first filesystem (partition) to check;
2 means all other filesystems to be checked.

Your root partition *should* always be set to 1, and all other partitions (except for the swap, of course) *should* be set on 2. 

It's ok, you have your / partition set on 1 already:
```
# /dev/hda5
UUID=68cca515-1304-4c1d-b78e-e3c6ae3d62cc / ext3 defaults,errors=remount-ro 0 [COLOR="Red"]**1**[/COLOR]
```

So, the first line above will set the fsck check every boot; you could reboot now and see what the fsck check returns (if it finds errors, it *should* correct them automatically). 

After you reboot, you can use the second line above if you want to force fsck only at the 30th boot. (This is the default, anyway.)

Good luck !

LLRNR

---

