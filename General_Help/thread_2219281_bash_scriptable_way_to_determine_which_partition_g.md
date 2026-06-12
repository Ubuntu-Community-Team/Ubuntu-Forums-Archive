---
title: "bash scriptable way to determine which partition grub is looking in for stage 2 files"
date: 2014-04-23
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-04-23
At some point in the boot process, grub looks beyond the non-partition space on the outer rim of the drive and looks for config files (and code?) in one of the file systems in a partition before proceeding. I need a bash scriptable test to show which partition it is currently set to look in. I can't just test for the presence of /boot/grub or or similar files because any or all of the filesystems might have once been the one grub looked to and those files will still be there albeit unused.

When I need to do this test the machine will be up and running, fully booted from one of the file systems, which may or may not be the file system I need to identify. If you know the history of the system it is easy enough to
do manually but I'm looking for a foolproof way to automate it.

Thanks for reading. Suggestions?

---

### Post by Dreamer Fithp Apprentice on 2014-04-25
Pursuing this I found bootinfoscript (it's in the repository). Sure looks like it ought to lead to what I"m after. And when I ran it there was a line in the output file that ALMOST looked usefull:```
Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
```

"partition 94"? 94?!?!
I only have 8!
"for ."? .?!?!
To me "." either is a synonym for $PWD or is an ordinary punctuation mark terminating a declarative sentence. The latter sounds more likely in this case. That would seem to imply there was some variable there that was supposed to be expanded to make this into a meaningful sentence, but never got set. So I decided to read the script (since the name implies it is a script). Whereis gave me the location and I opened it in evim. In a commented out preamble it had ```
# The birth of Boot Info Script:
#  http://ubuntuforums.org/showthread.php?t=837791      

```
So I followed that to the ancient closed thread. I'm surprised my earlier searches hadn't turned it up because the title sure sounded promising: "
**[FONT=arial black][SIZE=1][SOLVED] How to determine which Linux partition w/ Grub controls the MBR?         "[/SIZE][/FONT]**

(I can't seem to shrink that font size - sorry for shouting) but of course it was all about grub "1". Nevertheless, it had this command which seemed worth a try:```
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
```but the output it gave me disn't seem to fit into the method of interpretation indicated there:```
2+0 records in
2+0 records out
2 bytes (2 B) copied, 0.000104627 s, 19.1 kB/s
0000000 ffff                                   
0000002

```
That's where I am now. I searched the peculiar string in the output file of bootinfoscript - "Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of  the same hard drive for core.img. core.img is at this location and looks in partition 94 for ." and while I found it quite a few times where people were posting the entire text of that output file, with the same number yet, but no indication of what it meant.

If any of that means anyting to anybody I'd appreciate being pointed in a promising direction. Thanks.

---

### Post by Dreamer Fithp Apprentice on 2014-04-27
Beginning to look like this is a bug, finagle knows in what package, that's been around since raring but was not present in Precise. The bootinfoscript started giving this error then. Elsewhere I came across the idea that grub.cfg needed some ()s inside the ' s in expressions like```
root='whatever'
```changing them to```
root='(whatever)'
```But I tried that and it made no difference.

I'm thinking I may install Precise on another partition just to get the older grub version. Maybe I can find a way to install grub from a precise live disk without having to install the whole OS. Or maybe there is some way I can downgrade grub-pc to an earlier version. But whichever way I do it, I'll have to figure out how to keep update from trying to change it. If anybody has a ghost of a clue on any of this I'd appreciate it.

---

### Post by oldfred on 2014-04-27
Boot-Repair also uses bootinfoscript.

But all the recent versions of grub have moved things around and bootinfoscript has not been updated for the newest versions of grub. Becomes a lot of different versions to test.

But I think the real code is now in core.img which is in the sectors right after the MBR. 
But if you have UEFI it is a whole different animal.

But it can also matter which drive. BIOS writes info on boot drive. I have my system set to boot sdd by default but have different recent versions of grub in all my other drives. My sdd is booting 12.04 and all the others are booting installs of 14.04 in various partitions.

---

### Post by Dreamer Fithp Apprentice on 2014-04-28
Thanks, Oldfred. That's very interesting about core.img. But for what I'm trying to do I don't think I need to worry about stuff that's in the space before the first partition, only the stuff in the partitions. I know about files in /boot/grub and /etc/default; there might be others I don't know about. Assuming all installed OSs in a given rig have a set of files like that (which isn't unrealistic - I think that would be the case if they were all installed by accepting the defaults about grub installation at the end of a regular cd-based installation) the problem is to decide which set is being used, and doing it in a scriptable way. Maybe I could get that by comparing access times. I think normally it should be whichever system was installed from scratch last with grub being installed as part of the process. But what if grub is purged and re-installed from the command line for instance? I think I'll look at the access time approach.

---

### Post by oldfred on 2014-04-28
I have 4 hard drives plus several flash drives with grub fully installed.

And sda boots test beta updated to current 14.04 in sdc, sdb boots gubuntu in sdc, sdc boots new install of  14.04 in my SSD in sdd4, and sdd boots sdd3 my working 12.04.
 [http://paste.ubuntu.com/7302371/](http://paste.ubuntu.com/7302371/)


How will you check for that? I have so many old installs in sdc that I have real trouble keeping track. And first thing I have to do is turn off os-prober as it takes forever and makes a huge grub.cfg.

---

### Post by Dreamer Fithp Apprentice on 2014-04-28
Thanks again. I see what you mean. I've made the unexamined assumption that boot order is stable and that ain't necessarily so. I'll have to think about that a while to see what it implies.

---

### Post by oldfred on 2014-04-28
I was looking up some else and ran across this in my notes.

Herman's explanation of some details.
[http://ubuntuforums.org/showthread.php?t=1378527&p=9067452#post9067452](http://ubuntuforums.org/showthread.php?t=1378527&p=9067452#post9067452)

---

### Post by Dreamer Fithp Apprentice on 2014-05-07
Thanks again, Oldfred. I will study that. I've pursued this a little further in a different forum. Turns out there is a fork of bootinfoscript that works a little better. It still fails to give the drive, which again looks like some variable didn't get set. The relevant part of the output is:

" . . . and looks for (,msdos1)/boot/grub."

But you'll notice it DOES get the partition, which is a big improvement over what the one in the repository does. I plan to study the script. Maybe I can figure out what's wrong with it. (But I wouldn't advise anyone to bet on that.) Anyone interested can find more here:

[http://lists.gnu.org/archive/html/help-grub/2014-05/msg00025.html](http://lists.gnu.org/archive/html/help-grub/2014-05/msg00025.html)

---

### Post by oldfred on 2014-05-07
I have not seen Gert around working on Bootinfo script. He took over from meierfra.
Yann with Boot-Repair uses bootinfoscript but adds a lot more info and he is not as active as he once was. I did find out he got a job and new child about a year ago. 

But every release update to grub seems to move the byte(s) where drives and partitions are in program so script needs updating. 
But whoever works on script needs to know inner workings of BIOS & now UEFI and how they copy hardware data to drive and then how grub reads that and where in grub is the info on drive & partition with its install.

---

