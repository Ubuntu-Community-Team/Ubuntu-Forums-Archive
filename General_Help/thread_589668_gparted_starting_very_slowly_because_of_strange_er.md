---
title: "gparted starting very slowly because of strange error"
date: 2007-10-24
forum: General Help
---

### Post by Bert_2 on 2007-10-24
Already since I used the gutsy liveCD I'm having a strange problem with gparted. It is starting very very slowly, it keeps on scanning for several minutes before it finally shows my partition setup.
The strange thing is that I never had this problem when I was running feisty.

The errors I get when I call gparted from the command line are th following:
Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.
Unable to open /dev/fd0 - unrecognised disk label.

Though I have been working with ubuntu for more then 1,5 year now, I have never heard of fd0...

Perhaps you need the blkid output, so here it is:

bert@berts-desktop:~$ blkid
/dev/sda1: UUID="C2A87C28A87C1D5B" LABEL="Lokaal station" TYPE="ntfs" 
/dev/sdb4: UUID="E4DC-DE6C" TYPE="vfat" 
/dev/sdb5: UUID="32541d63-577f-4a17-b72b-7cffdff7eba9" TYPE="swap" 
/dev/sdb6: UUID="3752f7aa-693a-4a3b-93b1-6cea9bf6e1d7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="784784b0-a447-405d-b98d-82ce5dbd3f0e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb8: UUID="ec5b0fbf-a95d-437f-a24f-1abf3fe6981e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="HDD C-35" UUID="4616-4E83" TYPE="vfat" 


I hope someone can tell me whether this is a bug or a hardware error ;)

---

### Post by Sef on 2007-10-24
Seems like the disk is bad, so download [GParted,]("http://gparted.sourceforge.net") itself and use that.

fd0 is the floppy disk.

---

### Post by Bert_2 on 2007-10-24
I reinstalled the packages gparted, parted and libparted but my gutsy installation is still displaying the same errors, sorry...

---

### Post by btk on 2007-10-27
To get around this disable the floppy drive in your BIOS.

If you can't do that just disconnect the thing.

No more readonly fd0 messages.

---

### Post by Bert_2 on 2007-10-28
okey, /thx btk. I'll try that as soon as I'm home next week ;)

---

