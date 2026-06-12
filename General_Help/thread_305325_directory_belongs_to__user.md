---
title: "directory belongs to ? user"
date: 2006-11-23
forum: General Help
---

### Post by georgie on 2006-11-23
Hiya


I have a couple of directories on my /data partition that don't belong to any user.

#ls -la

?---------   ? ?      ?              ?                ? big_flame
?---------   ? ?      ?              ?                ? big_star

These are causing me big problems. If I ls -ls on them, the ls process takes 100% CPU and hangs.

I've tried to chown then, delete them, etc etc - both as myself, and root (via sudo and as actual root) - to no avai

root[mp3]# chmod 777 big*
chmod: cannot access `big_flame': Permission denied
chmod: cannot access `big_star': Permission denied

root[mp3]# chown 777 big*
chown: cannot access `big_flame': Permission denied
chown: cannot access `big_star': Permission denied

root[mp3]# rm -rf big*

(..hangs...)

#top
29051 root      25   0  2868  624  524 R  100 (CPU usage) 0.0   0:27.33 rm    





I don't really care about the contents of them (although it'd be nice to not have to delete them) but would like them to be owned by me, or deletable.

Anyone got any thoughts?

Regards

George

---

### Post by yota on 2006-11-23
Mhh... pretty strange, first I would check the filesystem consistency with fsck; if /data is on your root filesystem you can program a scan at boot time with:
```

sudo touch /forcefsck

```
then I'll try to see if those dirs have extended attributes set:
```

lsattr big*

```
Let me know!

---

### Post by taurus on 2006-11-23
What if you change the owner and permissions on those two directories from a terminal, Applications -> Accessories -> Terminal?

```
sudo chmod 755 *
sudo chown john:john *
(assuming john is your login name...)
```

---

### Post by georgie on 2006-11-23
Hi all

taurus - did that, as i said in the first post. No joy
yota - did what you said, fsck ran OK. No joy with the second command - 

#sudo lsattr big_star 
lsattr: Permission denied while trying to stat big_star

any more thoughts? this is baffling me...

---

### Post by taurus on 2006-11-23
Did you get any error message when you ran those two commands?

---

### Post by georgie on 2006-11-23
yes - did you read my 1st post :)

root[mp3]# chmod 777 big*
chmod: cannot access `big_flame': Permission denied
chmod: cannot access `big_star': Permission denied

root[mp3]# chown 777 big*
chown: cannot access `big_flame': Permission denied
chown: cannot access `big_star': Permission denied



root[mp3]# chown -R george:users big*
chown: cannot access `big_flame': Permission denied
chown: cannot access `big_star': Permission denied

---

### Post by taurus on 2006-11-23
> **georgie said:**
> yes - did you read my 1st post :)

root[mp3]# chmod 777 big*
chmod: cannot access `big_flame': Permission denied
chmod: cannot access `big_star': Permission denied

root[mp3]# chown 777 big*
chown: cannot access `big_flame': Permission denied
chown: cannot access `big_star': Permission denied



root[mp3]# chown -R george:users big*
chown: cannot access `big_flame': Permission denied
chown: cannot access `big_star': Permission denied


Well, apparently NOT because I had a "sudo" in front of those two commands!!!  ](*,)

---

### Post by georgie on 2006-11-23
This is what I'm trying now

After umounting the partition I'm running reiserfsck on it.

 sudo reiserfsck /dev/hdd1 --rebuild-tree

this is what it's finding so far. Let's see...

reiserfsck --rebuild-tree started at Thu Nov 23 13:46:36 2006
###########

Pass 0:
####### Pass 0 #######
Loading on-disk bitmap .. ok, 40959732 blocks marked used
Skipping 9617 blocks (super block, journal, bitmaps) 40950115 blocks will be read
0%....20%..block 14507266: The number of items (32782) is incorrect, should be (1) - corrected
block 14507266: The free space (628) is incorrect, should be (3088) - corrected
pass0: vpf-10110: block 14507266, item (0): Unknown item type found [2984666612 25691778 0x8007082af00350 ??? (8)] - deleted
..block 18168051: The number of items (50944) is incorrect, should be (1) - corrected
block 18168051: The free space (14469) is incorrect, should be (3792) - corrected
pass0: vpf-10110: block 18168051, item (0): Unknown item type found [948241392 973078527 0x10000008a860fd0 ??? (8)] - deleted
40%....pass0: vpf-10440: block 26542120, item 6: Wrong order of items - change the dir_id of the key [35282 36167 0x0 SD (0)] to 35282
pass0: block 26542120, item 5 (upper): Item [35285 35293 0x1 IND (1)] is out of order - deleted
pass0: vpf-10460: block 26542120, item 4: Wrong order of items - change the dir_id of the key [35285 35293 0x0 SD (0)] to 35282
pass0: block 26542120, item 4 (lower): Item [35282 35293 0x0 SD (0)] is out of order - deleted
60%..                             left 12778841, 12454 /sec

---

### Post by georgie on 2006-11-23
taurus. I was runnning them as root - as it said.

thanks for suggestions though. Still baffled

---

### Post by yota on 2006-11-23
Hi georgie,

notice that to force fsck on a clean unmounted system you need to use the -f (force) swith otherwise fsck will only report that the fs seems ok.

Can you please post the fsck output?

---

### Post by taurus on 2006-11-23
Logging in as root!!!  That's sure one way to screw up the system fast?  What about this command?

```
ls -la /
```
Do you remember how you created those two directories under /data (as root again, I assume)?

---

### Post by taurus on 2006-11-23
Logging in as root!!!  That's sure one way to screw up the system fast?  What about this command?

```
ls -la /
```
Do you remember how you created those two directories under /data (as root again, I assume)?

---

### Post by georgie on 2006-11-23
Hey yota. I'll run fsck after the reiserfsck --rebuild-tree completes and post response, cheers.

taurus. I'm not 'logged in as root.' I've tried both with sudo and sudo bash, in case there was something specifically weird about the user permissions stuff.

'Do you remember how you created those two directories under /data (as root again, I assume)?'

No. These are my data directories. They're created by me - years and years ago.

'Logging in as root!!! That's sure one way to screw up the system fast?'

? No it isn't. This looks like a low-level problem, possibly inode related. Fscking and the like *are* ways to mess up the system, root or otherwise :) - but it looks like this is what I'll need to fix this. Google hasn't been able to help me.

---

### Post by georgie on 2006-11-23
OK, this fixed it :)

george[~]$ sudo reiserfsck /dev/hdd1 --rebuild-tree
reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

*************************************************************
** Do not  run  the  program  with  --rebuild-tree  unless **
** something is broken and MAKE A BACKUP  before using it. **
** If you have bad sectors on a drive  it is usually a bad **
** idea to continue using it. Then you probably should get **
** a working hard drive, copy the file system from the bad **
** drive  to the good one -- dd_rescue is  a good tool for **
** that -- and only then run this program.                 **
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to [email]reiserfs-list@namesys.com[/email], **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  [www.namesys.com/support.html](www.namesys.com/support.html). **
*************************************************************

Will rebuild the filesystem (/dev/hdd1) tree
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
Replaying journal..
Reiserfs journal '/dev/hdd1' in blocks [18..8211]: 0 transactions replayed
###########
reiserfsck --rebuild-tree started at Thu Nov 23 13:46:36 2006
###########

Pass 0:
####### Pass 0 #######
Loading on-disk bitmap .. ok, 40959732 blocks marked used
Skipping 9617 blocks (super block, journal, bitmaps) 40950115 blocks will be read
0%....20%..block 14507266: The number of items (32782) is incorrect, should be (1) - corrected
block 14507266: The free space (628) is incorrect, should be (3088) - corrected
pass0: vpf-10110: block 14507266, item (0): Unknown item type found [2984666612 25691778 0x8007082af00350 ??? (8)] - deleted
..block 18168051: The number of items (50944) is incorrect, should be (1) - corrected
block 18168051: The free space (14469) is incorrect, should be (3792) - corrected
pass0: vpf-10110: block 18168051, item (0): Unknown item type found [948241392 973078527 0x10000008a860fd0 ??? (8)] - deleted
40%....pass0: vpf-10440: block 26542120, item 6: Wrong order of items - change the dir_id of the key [35282 36167 0x0 SD (0)] to 35282
pass0: block 26542120, item 5 (upper): Item [35285 35293 0x1 IND (1)] is out of order - deleted
pass0: vpf-10460: block 26542120, item 4: Wrong order of items - change the dir_id of the key [35285 35293 0x0 SD (0)] to 35282
pass0: block 26542120, item 4 (lower): Item [35282 35293 0x0 SD (0)] is out of order - deleted
60%....80%....100%                       left 0, 11454 /sec
60298 directory entries were hashed with "r5" hash.
        "r5" hash is selected
Flushing..finished
        Read blocks (but not data blocks) 40950115
                Leaves among those 56969
                        - corrected leaves 1
                        - leaves all contents of which could not be saved and deleted 2
                Objectids found 60285

Pass 1 (will try to insert 56967 leaves):
####### Pass 1 #######
Looking for allocable blocks .. finished
0%....20%....40%..pass1: block 23658519, item 2, entry 3: The entry "02-billy_braggbetween_the_wars.mp3" of the [35282 36075 0x1 DIR (3)] has hash offset 191741312 not larger smaller than the previous one 1079862144. The entry is deleted.
pass1: block 23658519, item 2, entry 3: The entry "Talking with the Taxman About Poetry" of the [35282 36075 0x1 DIR (3)] has hash offset 197777152 not larger smaller than the previous one 1079862144. The entry is deleted.
..60%....80%....100%                         left 0, 379 /sec
Flushing..finished
        56967 leaves read
                56932 inserted
                35 not inserted
####### Pass 2 #######

Pass 2:
0%....20%....40%....60%....80%....100%                           left 0, 0 /sec
Flushing..finished
        Leaves inserted item by item 35
Pass 3 (semantic):
####### Pass 3 #########
/mp3/billy_braggvpf-10680: The directory [35282 36226] has the wrong block count in the StatData (5) - corrected to (3)
vpf-10650: The directory [35282 36226] has the wrong size in the StatData (2072) - corrected to (1336)
/mp3/2_lone_swordsmen/05 Sex Beat.mp3vpf-10680: The file [35285 35293] has the wrong block count in the StatData (16032) - corrected to (13352)
/mp3/big_audio_dynamitevpf-10680: The directory [35282 36075] has the wrong block count in the StatData (3) - corrected to (1)
vpf-10650: The directory [35282 36075] has the wrong size in the StatData (1456) - corrected to (160)
Flushing..finished                                                             
        Files found: 56317
        Directories found: 3622
        Symlinks found: 317
        Others: 2
Pass 3a (looking for lost dir/files):
####### Pass 3a (lost+found pass) #########
Looking for lost directories:
Looking for lost files:0 /sec
Flushing..finished2, 848 /sec
        Objects without names 26
        Empty lost dirs removed 1
        Files linked to /lost+found 26
Pass 4 - finished       done 0, 0 /sec
        Deleted unreachable items 2
Flushing..finished
Syncing..finished
###########
reiserfsck finished at Thu Nov 23 14:50:13 2006

ls -la big*

big_flame:
total 50688
drwxrwxrwx   2 george george     904 2006-04-16 07:25 .
<snip>

big_star:
total 15
drwxrwxrwx   4 george george   104 2006-04-16 07:25 .
drwxr-xr-x 412 george george 14448 2006-11-23 11:07 ..
drwxrwxrwx   2 george george    48 2006-04-16 07:25 in_space
drwxrwxrwx   2 george george   952 2006-04-16 07:26 sister_lovers

---

### Post by yota on 2006-11-23
Oh sorry, forget about -f. I assumed you were using ext3. -f is just ignored by fsck.reiserfs and --rebuild-tree is probably the right way to go.

Let's know how it ends.

---Edit: I hate simulposting, but happy to see you've fixed it.

---

### Post by georgie on 2006-11-23
me too. weird problem, huh?

thx y'all for suggestions.

georgie

---

