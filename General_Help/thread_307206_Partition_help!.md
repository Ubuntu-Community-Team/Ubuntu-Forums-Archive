---
title: "Partition help!"
date: 2006-11-26
forum: General Help
---

### Post by Kittie Rose on 2006-11-26
I cleared up my "Middle" partition in windows, G:, my other two are C and H which contain important Data and everything I removed from G that I didn't delete. When I was going through the partition program it appeared to detect this as the partitions matched up in size; but now I'm at the "Prepare mount points" and it doesn't seem to let me focus on just one partition(or tell me how to set up the swap partition). I don't know what to do! I don' want to overwrite data. Please tell me what to do before I mess everything up badly. How do I make absolutely sure it doesn't touch C: and H:? I need to split my G: Partition for a swap too as I don't have another one. 

I need to dual boot with Windows as there are some games and apps I still need windows for...

---

### Post by taurus on 2006-11-26
Ubuntu needs to create two partitions, one for / and one for swap.  Therefore, it's better to use the last partition in your drive to install Ubuntu.  So, you may want to move your data from H: to G: and tell the installer to use the H: partition install Ubuntu on it.  In the meantime, what is the output of this command from a terminal?

Applications -> Accessories -> Accessories
```
sudo fdisk -h
```

---

### Post by zgornel on 2006-11-26
Let me see if I understood well: you are installing ubuntu, have 2 partitions <C><free space><H>. You want to install linux in the middle free space. 
Just create a partition in the free space - mount point "/", (select the ext3 format), resize it (leave about 1gb for swap), create a swap partition (select the linux-swap format). For the windows partitions, select as mountpoints /media/C-win and /media/H-win. I think you can edit the mount points yourself. Mount points are just the directories where you'll find the data of these partitions. Nothing should be lost.
Edit: If in the middle there is no <free space> but <G>, delete first G.

---

### Post by Kittie Rose on 2006-11-26
I can't move stuff from H to G - there is not enough space on that Partition.

However, I don't believe I'm using the letter "F" for anything.

How do I resize the partitions? I'm in the partition manager thingie right now installing Ubuntu... I'm using Firefox off the Live CD.

---

### Post by zgornel on 2006-11-26
> **Kittie Rose said:**
> I can't move stuff from H to G - there is not enough space on that Partition.

However, I don't believe I'm using the letter "F" for anything.

How do I resize the partitions? I'm in the partition manager thingie right now installing Ubuntu... I'm using Firefox off the Live CD.
Right click the partition, Resize/Move - just drag left-right the right end. I don't remeber very well, I installed some time ago and never payed too much attention on this. Don't worry about letters, be careful on deleting the right partition, that's all.

---

### Post by Kittie Rose on 2006-11-26
Think I got it right, thanks :) My main problem was that there is no "THIS IS WHERE YOUR LINICKS IS GOING TO BE INSTALLED" sign. I'd recommend putting that in future versions...

Also, how do I change all the tan colours to shades of green..? I can only seem to select themes not edit or create them... I might install KDE at some point if I get sick of GNOME.

---

### Post by strangelife on 2006-11-26
> **Kittie Rose said:**
> Think I got it right, thanks :) My main problem was that there is no "THIS IS WHERE YOUR LINICKS IS GOING TO BE INSTALLED" sign. I'd recommend putting that in future versions...

Also, how do I change all the tan colours to shades of green..? I can only seem to select themes not edit or create them... I might install KDE at some point if I get sick of GNOME.

Man this is cool !

---

