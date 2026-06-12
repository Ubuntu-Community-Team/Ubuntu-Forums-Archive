---
title: "/home on it's own partition"
date: 2008-06-05
forum: General Help
---

### Post by dont_give_me_that_look on 2008-06-05
Hey. I know that there are topics about this, but none of them helped me and I am too pissed off to search any further, so I'll make my own. I have 3 simple questions:

1. Why the hell doesn't Ubuntu automatically make an own /home partition? It didn't say anything about it during the installation, so I assumed that the installer is smart enough to do it for me.

2. How do I move my /home to another partition? I created the new partition with the Live CD, but I don't know how to move the folder correctly.

I found this tutorial:[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) but it doesn't work.
When I enter the cpio command it gives me "invalid option -- e". Can I please have a working step-by-step guide?

3. Just curious, is there a way to assign /home to an own partition during the installation?



edit: Thanks everyone, problem solved. Everything runs perfect now. Would still be nice to have an installation prompt that asks if you want your personal data on a seperate partition.

---

### Post by Xiong Chiamiov on 2008-06-05
1.  For people like me.  I fill up my /home with lots of stuff, but I install apps almost every day as well, so I don't know the proper proportions to make my partitions.  Thus, I keep it on one.
2.  Mount the partition somewhere temporarily, then
```
mv -r /home /[temporary mount point]
```
Then change your GRUB menu so that it mounts the /home folder from the new partition.
3.  I believe that /home is one of the options you can select when choosing where to mount the partitions.  I haven't ever installed Ubuntu, though, and I don't know how similar the installer is to those of Kubuntu and Xubuntu.

EDIT: Ah, I see.  For #2 they want to copy over softlinks as well.  How are you getting an invalid --e error if there's no --e option in that command?

---

### Post by dont_give_me_that_look on 2008-06-05
> **Xiong Chiamiov said:**
> For #2 they want to copy over softlinks as well.  How are you getting an invalid --e error if there's no --e option in that command?

I really don't know.

```
user@user:/home$ find . -depth -print0 | cpio -null -sparse -pvd /mnt/newhome/
cpio: invalid option -- e
Try `cpio --help' or `cpio --usage' for more information.
```

The command is right, isn't it?

---

### Post by dont_give_me_that_look on 2008-06-05
Seriously, I'll keep this topic going until the problem is solved. This is annoying.

---

### Post by drs305 on 2008-06-05
Here is a good guide to moving the home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

> Just curious, is there a way to assign /home to an own partition during the installation?

During the installation process, you have an option to manually partition your drive. If you select new partition, there is a window next to "Mount Point". When you click on the empty window one of the selections is "*/home*".

---

### Post by plucky on 2008-06-05
> user@user:/home$ find . -depth -print0 | cpio -null -sparse -pvd /mnt/newhome/

That line should look like this:-


```
find . -depth -print0 | sudo cpio --null --sparse -pvd /mnt/newhome/
```


See this link [on Psychocats website](http://www.psychocats.net/ubuntu/separatehome) for creating a separate home partition.


> 3. Just curious, is there a way to assign /home to an own partition during the installation?

Yes there is.When you created the **/** partition,you can also create a separate **/home** partition plus any other partition you want (e.g /usr, /var, /boot, ) 

Good Luck

---

### Post by mrMango on 2008-06-05
The installer does not make it's own home partition because most people do not need home on its own partition. You can, however, override the installer by not selecting guided partition setup, and creating a partition to be mounted in /home. See [this]("http://neosmart.net/wiki/download/attachments/9764870/Create%20Partition.png") image: one would change the mount point to /home

For moving after the install: Once you've sized a partition for home and created a filesystem on it, you can simply move /home there. For example, if /dev/sda3 was the new home partition

```
mke2fs -j /dev/sda3
mkdir /mnt/tmp
mount /dev/sda3 /mnt/tmp
cp -av /home/* /mnt/tmp/
```

I use cp because moving your /home while you're actually logged in is probably nasty. You'll then have to edit /etc/fstab (not GRUB) to have the partition auto mounted on bootup. See [FONT="Courier New"][man fstab]("http://linux.die.net/man/5/fstab")[/FONT]. After everything is done, you should remove the contents of your home directory:

```
umount /mnt/tmp
rm -Rf /home/
```

Reboot and it should work. Symlinks should copy fine because the location of your home directory hasn't changed, only where the files are physically located. That's one of the advantages of mounting filesystems and having symlinks rather than file-based links and drive letters (looking at you, Windows).

---

### Post by Sef on 2008-06-05
> During the installation process, you have an option to manually partition your drive.

Manually partitioning is not hard, but it is a bit tricky the first time or two.

---

### Post by dont_give_me_that_look on 2008-06-05
That's true, but I assumed that it would all be done automatically when I give Ubuntu control over the whole disk.

Re-Installing doesn't take very long so I decided to go for that. Will this setup work out, or is it better to put the swap into the first or last place?

[http://img292.imageshack.us/img292/2872/screenshotet1.png](http://img292.imageshack.us/img292/2872/screenshotet1.png)

Thanks for the replies everyone.

---

### Post by mrMango on 2008-06-05
The problem with using that setup is you may run out of space on one partition and not another. There's nothing wrong with putting swap in the middle; that's what I do. For now, that'll work swimmingly.

You may be interested in reading up on LVM2 in the future though, which allows dynamically resizing partitions on the fly.

---

