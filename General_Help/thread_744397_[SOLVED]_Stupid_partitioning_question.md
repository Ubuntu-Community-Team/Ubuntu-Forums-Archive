---
title: "[SOLVED] Stupid partitioning question"
date: 2008-04-03
forum: General Help
---

### Post by jakupl on 2008-04-03
I feel like making the swap larger... just for the feeling of it... but I dont know how.

I'm trying to use gparted.
When I press "swapoff" I can't make it larger... I assume this is because there is no free diskspace left. I guess i have to shrink my harddisk to enlarge the swap, for this I have to unmount the harddisk...

so my question is, can I unmount my only harddisk.... or is that needed? I fear that my computer will go blank if i do it :lolflag::confused:

[IMG]http://i228.photobucket.com/albums/ee289/jakupl/Screenshot--dev-hda-GParted.png[/IMG]

---

### Post by jakupl on 2008-04-03
or do I need the live cd to do this?

---

### Post by adamitj on 2008-04-03
Man...  by my own experience... 

Most important than the OS reliability cames the hardware reliability. Many factors can bug you data on disc, so I recomend you to make a full backup of your important files.

Therefore, to resize your swap, if you can do it by Live CD as you presume, doing this:

1) remove hda5
2) remove hda2
3) resize hda1
4) recreate hda2 as extended partition
5) recreate hda5 with the new size as SWAP

Notice this actions still by your own responsability, so backup is essential.

---

### Post by jakupl on 2008-04-03
Thankyou very much. however I didn't bother to remove hda5 and hda2.
I just resized hda1 and 5 and 2 all in one :)

great stuff... I now have 5,55 Gb of swap... Alot more than I need :lolflag:

---

### Post by s3a on 2008-04-03
Anything more than 1 GB of swap is a waste in my opinion...you should have a swap that's exactly 1GB.
I have 1GB of real RAM and have never reached my limit in capacity and I have many firefox windows open and each firefox window has many tabs. I have music, several thousand applications, etc open as well not to mention, I had compiz at max, everything jellowed, even the menu! I'm just trying to help you not waste unecessary space and I was hoping an example could show you right from wrong ;).

---

### Post by jakupl on 2008-04-03
yeah.. But this was just for fun... I have enough of hd space... I can just resize if it becomes a problem :)

thanks for your help.. now I atleast know how to do it.

---

### Post by jakupl on 2008-04-03
however, now I face another problem, now I have to manually press "swapon" everytime I boot. swap is automatically inactive when i start the computer... any suggestions? :confused:

---

### Post by jakupl on 2008-04-04
kadabump

---

### Post by Rigrig on 2008-04-04
Could you post the contents of the */etc/fstab* file? Somewhere in there should be an entry to mount the swap partition.
The line would probably look like either this:```
/dev/hda5 none swap sw 0 0
``` or this: ```
UUID=72b981f7-7ac6-403a-9c7d-408548401288 none swap sw 0 0
```
If it looks like the last one, the partition UUID was changed by the resizing, and you should be able to find the new UUID by opening a terminal and typing```
sudo blkid | grep swap
```
This should output something like```
/dev/hda5: TYPE="swap" UUID="72b981f7-7ac6-403a-9c7d-408548401288"
```

If this didn't help, posting */etc/fstab* here might provide us with some more insight into the problem.

---

### Post by matey3 on 2008-04-04
I am new to ubuntu but i think may be you can right-click on the swap part and then choose the swapon if it says swapoff?
i dont know if that has something to do with it or not? and not sure if the manage flag makes any difference?

---

### Post by jakupl on 2008-04-04
sudo blkid | grep swap gave me this:

```
/dev/hda5: TYPE="swap" UUID="628c6eaa-a4f2-48a7-a3e4-a3a2affdd3ef" 
```


this is my /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c98dfc78-177b-40f9-8013-6aea32a8c3d2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7117efda-f478-44ff-9aed-b37511c9f325 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

I dont understand one bit of it... help please :KS:confused::)

thankyou very much

---

### Post by fsmithred on 2008-04-04
Linux looks at fstab to decide what partitions get mounted at boot. It uses the UUID to identify the partitions. Your fstab shows the old UUID for hda5, and you need to replace it with the new UUID that you got from the blkid command (without the quotes) so that

```

UUID=7117efda-f478-44ff-9aed-b37511c9f325

```

becomes

```

UUID=628c6eaa-a4f2-48a7-a3e4-a3a2affdd3ef

```

---

### Post by jakupl on 2008-04-04
ok nice thankyou very much :)

why doesn't this happen automatically ?

---

