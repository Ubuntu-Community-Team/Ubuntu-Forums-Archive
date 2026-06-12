---
title: "EXT2-fs: corrupt root inode, run e2fsck fails"
date: 2007-03-27
forum: General Help
---

### Post by djamu on 2007-03-27
After a partition resize my 500GB USB disk refuses to mount, disk was ext3 partition, gparted now recognizes it as ext2

fsck /dev/sda1 gave me a lot a lot of "Group x's inode table at xxxxx conflicts with some other fs block.
Relocate<y>? "

aborted this and ran
fsck -y /dev/sda1 until " Root inode is not a directory. Clear? yes " Aaaaarg
h, damn ......
error 8 popped up, but left process running for 50 hours before quiting it (!) hoping it would be alright

some browsing on WWW revealed 
"Pass 1 takes the longest time to execute, since all of the inodes have to be read into memory and checked. To reduce the I/O time necessary in future passes, critical filesystem information is cached in memory. The most important example of this technique is the location on disk of all of the directory blocks on the filesystem. This obviates the need to re-read the directory inodes structures during pass 2 to obtain this information."

this is probably the reason why I got this error -not enough RAM-, as I connected the USB disk to my spare ( old ) laptop ( IBM thinkpad 256MB ram, runs otherwise very nicely with ubuntu ), 
 

```

root@ubuntu:/# mount /dev/sda1 /media/500gb/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
```

root@ubuntu:/# dmesg | tail
[17179650.572000] Bluetooth: L2CAP ver 2.8
[17179650.572000] Bluetooth: L2CAP socket layer initialized
[17179651.772000] Bluetooth: RFCOMM socket layer initialized
[17179651.772000] Bluetooth: RFCOMM TTY layer initialized
[17179651.772000] Bluetooth: RFCOMM ver 1.7
[17181754.432000] EXT2-fs: corrupt root inode, run e2fsck

```

testdisk reveals EXT2 Large file Sparse superblock, 497 GB / 463 GiB
gparted & qtparted are showing an ext2 partition

ran 
```

root@ubuntu:/home/jan# lde /dev/sda1
User requested autodetect filesystem. Checking device . . .
Found ext2fs on device.
Warning: First block (0) != Normal first block (1)
root inode isn't a directory

```

lde is probably able to correct this, but I thought it would be wise if one of  the gurus out there would help me out on this.
mmmm, windoz time
rlinux ( free application on [http://www.data-recovery-software.net/Linux_Recovery.shtml]("http://www.data-recovery-software.net/Linux_Recovery.shtml")
is able to recover about 70% of my data
Nucleus Kernel Linux ( not free, 49$  [http://www.nucleustechnologies.com/]("http://www.nucleustechnologies.com/") ) is able to recover ALL of my data

So it's not that my data is lost, it's just that i'm unable to repair this. 
Thinking it's probably just a flag in the root inode, as lde indicates - i'm comfortable with hex editors - made  me do an extensive search on www.  Unfortunately this reveals very little info on flag usage - I found 1 ! page ( in italian ) showing some  -

What annoys me the most is that although ext2/ext3 is a nix filesystem, I need windoz to recover my data.... [-X 

Any help ( flag diagrams, tools ) is highly appreciated

---

### Post by fanatik on 2007-03-27
have a look at dumpe2fs, it might help?

I'm not a filesystem expert, but was reading the man pages for fsck.e2fs, it also suggests that if you have a filesystem that can't be fixed, you should file a but report... 

Good luck!

James.

---

### Post by djamu on 2007-03-28
Thanks , used that also ( forgot to mention it )

Doesn't seem to be of any help -at least for me- either :( 
Clearly there's a filesystem, I just can't mount it 

```

root@ubuntu:/# dumpe2fs -h /dev/sda1 
dumpe2fs 1.39 (29-May-2006)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          0ef5a677-47fb-4bae-aee0-a25bc58bfd4a
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      resize_inode dir_index filetype sparse_super large_file
Default mount options:    (none)
Filesystem state:         not clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              60735488
Block count:              121453400
Reserved block count:     6072670
Free blocks:              10644662
Free inodes:              60563151
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1024
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Sat Feb 24 13:51:53 2007
Last mount time:          Wed Mar 14 17:16:31 2007
Last write time:          Wed Mar 14 17:30:45 2007
Mount count:              1
Maximum mount count:      29
Last checked:             Wed Mar 14 16:31:47 2007
Check interval:           15552000 (6 months)
Next check after:         Mon Sep 10 17:31:47 2007
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Default directory hash:   tea
Directory Hash Seed:      25354299-dd40-40db-928a-47b1cd3bf8b6
Journal backup:           inode blocks
Bad blocks: 7962656, 11239456, 20480032, 23887904, 71663648, 78676000, 102400032
root@ubuntu:/# 


```

---

### Post by fanatik on 2007-03-28
It seems you have some bad blocks, is your disk on the way out??

This is the top of my output:

```
[FONT="Courier New"]Filesystem volume name:   /usr/local
Last mounted on:          <not available>
Filesystem UUID:          dcc1afd5-15e3-44eb-81da-2e660032a3a2
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux[/FONT]

```

I also meant to say bug report in my previous post, not but report! :D

---

### Post by djamu on 2007-03-28
Thanks for the reply.

I also noticed those bad blocks, - there where more before - previous run of fsck stated they where wrongfully flagged as bad blocks.
 
"Programming error?  block #71663648 claimed for no reason in process_bad_block"
"Programming error?  block #78676000 claimed for no reason in process_bad_block."
"Programming error?  block #102400032 claimed for no reason in process_bad_block."
etc...

I guess the previous fsck run didn't make it until there.  Should make sense since the drive is only 1.5 months old and I seriously doubt if they really are corrupt.

---

### Post by djamu on 2007-04-02
started a couple of days ago fsck again 
```

fsck -y /dev/sda1

```it's been running ever since ( 109 hours now )

I have no clue if it's actually repairing my file system, aside from using a lot of resources ( memory & CPU ) running "top"

I posted this problem at the e2fsck creators site forum, but since there isn't much activity :( [https://sourceforge.net/forum/forum.php?forum_id=7053](https://sourceforge.net/forum/forum.php?forum_id=7053)

Anyone, please ?


Final result:

Stopped running it after 10 days [COLOR="Red"] 240 hours, [/COLOR], I got an idea that it is unable to fix it because the filesystem contains some image backups, that might be recognized.... darn.....
used a windows application -see top message - that was able to read it....

---

### Post by mrgod on 2007-07-15
I got just the same error, but on my ext3 formated disk. If you see at the number ex.:
"Group 2935's inode bitmap at **96174081** conflicts with some other fs block." you will probebly see the same number repeating it self.
I have no clue how to fix this, just hoping that someone will see this thread and help us out :)

---

### Post by Dusal on 2008-05-20
I just found this. Now I will try.

[http://www.linuxforums.org/forum/suse-linux-help/118214-solved-saving-data-broken-opensuse-partition.html](http://www.linuxforums.org/forum/suse-linux-help/118214-solved-saving-data-broken-opensuse-partition.html)

---

### Post by greco8523 on 2008-06-20
sounds like your drive is pretty bad, I would suggest imaging to a new drive with ddrescue then running some ext2 utulities to fix the corruption. 

Try this site for utilities: 

[http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html](http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html)

---

