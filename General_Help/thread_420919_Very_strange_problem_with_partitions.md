---
title: "Very strange problem with partitions"
date: 2007-04-24
forum: General Help
---

### Post by afr_q21 on 2007-04-24
Hi. First of all: I don't speak English perfectly, so I'll try to do my best.
I've been with this problem since more than 3 weeks, I'm a newbie and in the spanish forums nobody seems to know how to fix this (nor even in the web!).
The problem: I edited the file /etc/fstab, where I added information about partitions (ntfs & vfat) where I have all my files, documents, music, etc. The partitions get mounted when I start, but all files that have any Latin character on it (like ñ or accents) just don't show on nautilus, and it's impossible to open it from other applications (e.g. amarok doesn't load the playlist because the folder where I have my music has an accent). Thats only the beginning. The solution: I go to the shell and make a "sudo umount -a" and immediately a "sudo mount -a" and the problem is solved, I can access all my files, but never from the start.
Today my problem got worse, because I updated my system, and the NTFS-3G driver was updated too. Everything was running great, until I had to reboot... As I said, I made the umount/mount thing, and a message appeared saying that "this version of ntfs-3g needs the newer version of the FUSE module..." or something like, well I updated that FUSE following the instructions on the readme file included with this update of ntfs-3g, everything OK. So I rebooted again, made that umount/mount process and... everything was just like before, the same error, I reinstalled the FUSE many times without success.
Now, I want this to be clear: WHEN I START the system, the partitions get mounted  and they work well, but I can't access all my folders (because they are not there!). Then I make a umount/mount and my files appear, but I can't write, delete, and even open some file types on any ntfs partition (e.g. zip files), and this CAN be made BEFORE I umount the units.
Well... This is very frustrating and strange, and no matter how many modifications I do to the fstab, never works.
Here there is my /etc/fstab file as I have it now, I hope it can be solved:

******************************************************************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ca281ade-19a1-43c8-ae09-047fe94fd9fd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=5b3a3397-c8cc-4b25-8774-957241843470 /home           ext3 defaults,       0       2
# /dev/hda2
UUID=69c89a2d-91d2-48d9-9bf2-297269dc593b none            swap    sw              0       0
/dev/hdc        /media/cdrom0  udf,iso9660  utf8,user,noauto,     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

/dev/hda3 /media/Windows ntfs-3g utf8,defaults 0 0
/dev/hda6 /media/Intercambio vfat umask=000,exec,dev,suid,rw,auto,user,utf8 0 0
/dev/hdb1 	/media/Seagate ntfs-3g   utf8,defaults 0 0

********************************************************************************


I left the minimum options, but I've tried with so many (like the vfat partition) and no one worked.
Please, I hope somebody can help me.
Thank's!

---

### Post by paparucino on 2007-04-24
> **afr_q21 said:**
> 
I left the minimum options, but I've tried with so many (like the vfat partition) and no one worked.


I dont' know if this can help, but think that playing with "locale" can help

```

# Entry for /dev/hda1 :
UUID=CC5C765F5C7643EC /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1

```

---

### Post by afr_q21 on 2007-04-24
Hi paparucino, thank you for your answer. I did what you said but it doesn't works, everything is just the same.
What I did:
- First wrote exactly the same line you said
- Another try: I did the same but modifying the "locale=en_US.utf-8" with "locale=es_ES.UTF-8"
- Another try: I removed the utf 8 option that was already on my partition's options

But the problem is still exactly the same. Any other idea? Anyone else? 
Thanks a lot.

---

### Post by afr_q21 on 2007-04-24
Hi, I found a partial solution! I added the locale line to my partition options (keeping the line you said) and the partitions were well mounted at the begining, but I can't access my files because I think that the route assigned is wrong (e.g. the accents show well on nautilis, but in the paths to the files are substituted by other symbols) How can I edit the language preferences for the ntfs-3g? I think this can be the main problem.

---

### Post by paparucino on 2007-04-25
> **afr_q21 said:**
>  well on nautilis, but in the paths to the files are substituted by other symbols) How can I edit the language preferences for the ntfs-3g? I think this can be the main problem.
I think so. The only solution I know is to avoid the accents where you see there are problems.
I have a similar problem with mysql so I modiefied the field names using a' instead of à, e'-è and so on.
It's no a good solution, only a workaround

---

