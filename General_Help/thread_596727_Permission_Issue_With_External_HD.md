---
title: "Permission Issue With External HD"
date: 2007-10-29
forum: General Help
---

### Post by Zeenomorph on 2007-10-29
I know that there are quite a few posts about this, but I think that my situation is a little unique.

I have an external HD that I don't have permission for.  Now here's the catch; the drives name is "Mojo Giga Storage".  Yeah, spaces in the name.  I've had it for a while (since my Windoze days).  

It is NTFS.

I want to use it to back up my system so that I can upgrade to 7.10.

Thank you for any help that you can provide.

---

### Post by taurus on 2007-10-29
If it's ntfs filesystem, then you need to install and use ntfs-3g driver if you want to write to it.

```
sudo apt-get update
sudo apt-get install ntfs-3g ntfs-config
gksudo ntfs-config
```

---

### Post by Zeenomorph on 2007-10-29
I did that.  Seemed to work, but I still can't drag and drop onto the drive.  I can't paste into it, or delete from it.  

It has what it has, and can't be altered in any way.

---

### Post by Zeenomorph on 2007-10-30
Even selecting the permission tab is grayed out.

[ATTACH]48431[/ATTACH]

---

### Post by mjwebber on 2007-10-30
I am having the same kind of problem.  I have an external hard drive that, in my windows days, i was using to back up the system.  Now I am told that I don't have permission to use it.  I can get around access by pretending to be a root user.  But I cannot write to the drive and thus cannot back up any of my work.  Changing permissions is not permitted, since I am said not to be the owner of the drive.
What are the solutions to this kind of problem, please?  It seems from reading the threads that this kind of problem is not uncommon, but I have not seen any solution offered...

---

### Post by frodon on 2007-10-30
It's a common problem,first NTFS like FAT32 don't support right management and ownership so it is useless to try to change rights or ownership on these filesystems.
Second, for an external hard drive the most compatible file system is FAT32 though it is an older file system and have a 4Go max file size limitation.
Like taurus said use ntfs-config to enable write access to your ntfs drives, you may need to unplug your drive after this.

---

### Post by Zeenomorph on 2007-10-31
But that's exactly what I did.  I still can't do anything to the drive.  How can I back up my system?  Are portable HD's useless to Linux/Ubuntu?

---

### Post by Zeenomorph on 2007-11-01
Sorry to bumb my own thread.... but ..... Bumpity Bump Bump.

---

### Post by bingoUV on 2007-11-01
I see that the owner of the folder is root.
Can you try adding a file to the drive as root i.e.
```

cd /path/to/folder/where/drive/is/mounted
sudo touch testFileAsRoot

```

---

### Post by Zeenomorph on 2007-11-01
I would love to do that.  The issue is the name of my drive is "Mojo Giga Storage"  It has spaces (left over from Windoze).  So I can't get to it in terminal.

---

### Post by laluz on 2007-11-01
Hi there, 

I have the same problem and I have just tested the suggestion above. Zeenomorph, you may try doing the same way, by escaping the space with a backslash

cd /media/My\ Book/
sudo touch testFileAsRoot

A file testFileAsRoot was created. 
What next?

---

### Post by laluz on 2007-11-02
Where to configure the mount options for a pluggable drive? I assume, this must be set somewhere outside /etc/fstab ?

---

### Post by frodon on 2007-11-02
Either in fstab or in an autorun script in your external drives with the option "run autorun scripts when external storage device is plugged" enabled in the removable media window setting.

---

### Post by Zeenomorph on 2007-11-02
I may have been too hasty with the whole "It doesn't work" thing.  I feel foolish, but after a restart.... it works!

Time to upgrade to 7.10.  Lets hope that I'm not back here writing another message soon.

---

