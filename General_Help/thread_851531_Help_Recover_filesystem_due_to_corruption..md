---
title: "Help: Recover filesystem due to corruption."
date: 2008-07-06
forum: General Help
---

### Post by kingtaurus on 2008-07-06
Hi,

So here goes, my root partition (formatted in JFS) seemed to be having issues reading some specific files on the hard-drive. So I rebooted, entered recovery mode, remount the '/' in 'ro' and proceeded to run fsck.jfs on the drive. It found corruption on the drive and also found some bad blocks.

It recovered the files to lost+found. However, I didn't realize that the files recovered included the etc directory (so upon reboot ... I get a kernel panic - no init files).

Right now, I'm left with lost+found directory filled with copies of what was in various inodes (files named I001204.RCN, and these files correspond to a file that was in /etc and that were recoverable) and directory tree with names (D004173.RCN ... however descending into this directory, the file structure and naming is consistent (i.e. instead of D<some number>.RCN ... its the appropriately named directory and files). 

So I need some help figuring out a command to determine what the original name of the directory was to recreate my etc directory. Basically ... I can copy lost+found over to /etc ... but then I need to change the name of all the directories and files to the appropriate names.

Right now I'm using (using ubuntu install cd for a recovery disc):
```

sudo su
<mount the drive> mount -t jfs /dev/sdb3 /media/disk-2
cd /media/disk-2/lost+found
for x in `ls | grep -v I` do echo "DIRECTORY="$x; ls $x; done

```
I'll attach the output from the command in my next post.

---

### Post by kingtaurus on 2008-07-06
Here is the file I promised earlier (I had to tar the file because the size was larger than 19.5 KiB allowed for a txt file :( ).

---

### Post by kingtaurus on 2008-07-06
I'm just going to re-install ubuntu. It looks like the only way of saving all the files it to go through each file and directory and determining the appropriate directory name. The only issue, is I don't think I can tell (easily that I'm missing a file -- thus I'll re-install and use ext3 + run a bad blocks check).

---

