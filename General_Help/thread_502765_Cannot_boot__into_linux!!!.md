---
title: "Cannot boot  into linux!!!"
date: 2007-07-17
forum: General Help
---

### Post by kdarkentity on 2007-07-17
My problem is simple ...i cannot boot into linux!! ...when i try to boot into linux a disk check is forced and i get an error stating that files on the disk are corrupt and it says something about a  duplicate error... is there anything i can do to save linux at all... or at least can i save some of my data anyway???

---

### Post by Al3xK3aton on 2007-07-17
What did you change that made the problem start happening?

---

### Post by jocko on 2007-07-17
Try booting a live cd and start a file system check from a terminal:
```
sudo fsck -fpC 0 /dev/sda1
```This will force a check and try to fix any errors it finds (the drive should not be mounted).

You'll probably need to change the "/dev/sda1" in the above command to the correct device name.
If you don't know you can figure it out from the output of ```
sudo fdisk -l
```

---

### Post by kdarkentity on 2007-07-17
ok ill try that... and the only things that i can think of on what messed it up are ...i tried downloading updates and it froze soo i simply closed update manager and shut down,but i have had some errors before that , that i noticed... like totem and gxine crashed as soon as i opened them...but i dont really have any idea on how or what stopped me from being able to boot in...

---

### Post by kdarkentity on 2007-07-17
what do i do after i type  sudo fsck -fpC 0 /dev/sda1? ... this is the output i get

ubuntu@ubuntu:~$ sudo fsck -fpC 0 /dev/sda1 

fsck 1.40-WIP (14-Nov-2006)

Usage: fsck.ext3 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]

                [-I inode_buffer_blocks] [-P process_inode_size]

                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]

                [-E extended-options] device



Emergency help:

 -p                   Automatic repair (no questions)

 -n                   Make no changes to the filesystem

 -y                   Assume "yes" to all questions

 -c                   Check for bad blocks and add them to the badblock list

 -f                   Force checking even if filesystem is marked clean

 -v                   Be verbose

 -b superblock        Use alternative superblock

 -B blocksize         Force blocksize when looking for superblock

 -j external_journal  Set location of the external journal

 -l bad_blocks_file   Add to badblocks list

 -L bad_blocks_file   Set badblocks list

---

### Post by jocko on 2007-07-18
sorry, apparently fsck doesn't work with the option "-fpC 0"...
```
sudo fsck -fp /dev/sda1
``` will do the same, but you will not see any progress bar...

---

### Post by ubanchaos on 2007-07-18
well u might need to just format the hard drive and reinstall ubuntu.......windows is garbage anyways

---

### Post by kdarkentity on 2007-07-18
k thanks ill let you know if this helps

---

### Post by strabes on 2007-07-18
> **ubanchaos said:**
> well u might need to just format the hard drive and reinstall ubuntu.......windows is garbage anyways

That's not really necessary yet...

---

### Post by kdarkentity on 2007-07-22
Ok well i used your advice and kind of figured out what i needed to do by myself... what i did was boot into the recovery mode ...then run the command fsck ...than just keep saying yes to repair each error... now its running  just as new ....sooo im all set and thanks

---

