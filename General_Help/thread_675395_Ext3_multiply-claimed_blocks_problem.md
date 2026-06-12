---
title: "Ext3 multiply-claimed blocks problem"
date: 2008-01-22
forum: General Help
---

### Post by Qilz on 2008-01-22
Hello 

I have a problem with my ext3 file system, and although I can't ensure it is Ubuntu related, Ubuntu is what I use, so I cry here for help :) It's a long post, but I hope you will take the time if this is your expertise area.

So first - the problem:

After a reboot of my computer, fsck was forced due to the max mounting rule.
Fsck then list a _lot_ of inodes that contains "multyply-claimed block(s)".
After a lot of work, it starts listing me files that have multiply-claimed blocks and gives me the option of cloning the blocks, and if I don't want to do that, I can "delete the file".
A prompt looks like this:

[I]
File ??? (inode #39214, mod time Fri Sep 21 12:54:00 2007) 
  has 1 multiply-claimed block(s), shared with 1 file(s):
        ??? (inode #70666, mod time Fri Sep 21 12:54:00 2007)
Clone multiply-claimed blocks<y>? no

Delete file<y>? [/I]

Not all has the same filename (???) for both files, but it seems in most cases one of them has the name ??? or ... and the other is a named and known file.
All files seems to be old (last year).


So I have three questions I can't figure out:

1) How can the file system get so f... up so fast? (30 mounts before forced check, and it is mounted at least once a day)
2) If I select delete, which file will I delete, the first or the second one it lists.
3) Am I missing some easy n00b 'this will fix it' knowledge?

Here is my own thoughts

1) 
[LIST]
[*]I made a apt-get upgrade before the reboot, and that somehow created a problem (no idea how that should be possible though)
[*]Some time ago I did some resizing of old partitions and created a new partition. I did it in several 'steps'. So I did a manual resize of an ntfs system and used gparted (or qtparted) to create a new (and maybe some more resizing can't remember). If this wasn't done right, maybe some errors could show up later - though the file system seemed okay at the time... (this is probably the most likely cause, since I'm no file system expert and moved it around quite a bit)
[*]The disk is 4 years old - it could just be breaking down (it's a laptop)
[/LIST]

2) No idea

3) I have searched Ubuntu forums and Google etc and have only found questions, no answers. Most people also have only a few bad inodes, I have 3507 to be exact. And the people that fixed it has no idea what happened :)

Here are some similar topics:
[http://ubuntuforums.org/showthread.php?t=330129](http://ubuntuforums.org/showthread.php?t=330129)
[http://ubuntuforums.org/showthread.php?t=96133](http://ubuntuforums.org/showthread.php?t=96133)
[http://www.cowlug.org/pipermail/cowlug/2007-June/003958.html](http://www.cowlug.org/pipermail/cowlug/2007-June/003958.html)
[http://www.linuxquestions.org/questions/linux-general-1/file-system-corruption-causes-and-consequences-490404/](http://www.linuxquestions.org/questions/linux-general-1/file-system-corruption-causes-and-consequences-490404/)



Now, I have been able to mount the file system with a live cd, and take a backup of my home dir, so it wont be a big problem. Still, I would like to know what is going on. How could it happen?, how can I fix it? (if possible).
If anyone has any knowledge about this topic, I would greatly appreciate any help. And if you have a similar problem, please share it.

I know I could just do a fresh install, but I would rather learn something :) (besides that it is dangerous to play around with your partitions :) )

Regards
/Jacob


Other info:

I run Ubuntu 7.10

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1106     8883913+   7  HPFS/NTFS
/dev/sda2            3007        4772    14185395   83  Linux
/dev/sda3            4773        4864      738990   82  Linux swap / Solaris
/dev/sda4            1107        3006    15261750    7  HPFS/NTFS

(that + seems odd....)

---

### Post by dcstar on 2008-01-23
> **Qilz said:**
> 
........
So I have three questions I can't figure out:

1) How can the file system get so f... up so fast? (30 mounts before forced check, and it is mounted at least once a day)
2) If I select delete, which file will I delete, the first or the second one it lists.
3) Am I missing some easy n00b 'this will fix it' knowledge?
.......

1) Power failure, power shutdown before O/S shuts down correctly, hardware problems.

2) Don't know.

3) You can try turning off "Write Caching" on the hard disk, this will make it more reliable at the cost of lesser performance (use the **hdparm** command/configuration file).

---

### Post by Qilz on 2008-01-23
Thank you for your reply.

You are of course right that such errors can be created by turning off the power before the OS shutdown is complete. (and this might also have happened). But I just found it very unusual that 3000+ inodes would be broken this way. But I don't know exactly how the file system works - so I guess it could happen. I would think that it made changes in a more 'step by step' approach to avoid failures as large as this one, but then I guess hard disk caching could be the problem. (as you suggested - haven't thought of this).

The computer is four years old, and is a laptop, so the hard disk could contain errors. I have used the badblocks command (read only mode), but it found no errors. I also tried the smartctl command, also without indication of problems. Is this the way to check for errors on your harddisk? I found this list: 
[http://mirror.hamakor.org.il/archives/linux-il/11-2004/12635.html](http://mirror.hamakor.org.il/archives/linux-il/11-2004/12635.html)


So - I'm left with two open questions. Which file does fsck delete when I select delete, and what is the right way to go about recovering the file system.

I have already deleted some files and cloned some blocks (which was stupid of me, but it was before I realized that there was so many problems) so I will probably need to clean the system. But I would still like to find out what I should/could have done.

Again, any replies are greatly appreciated.

/Jacob

---

