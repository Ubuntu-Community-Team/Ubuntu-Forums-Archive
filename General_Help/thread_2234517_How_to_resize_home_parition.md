---
title: "How to resize home parition?"
date: 2014-07-15
forum: General Help
---

### Post by filipluch on 2014-07-15
Here is my partition table. How do I extend the last partition (sda8) using the unallocated space? It does not let me extend it.


[IMG]http://i.imgur.com/oFyzPI2.png[/IMG]

---

### Post by nerdtron on 2014-07-15
Unless an expert corrects me, I would say "You can't".

You can't join partitions with other partitions on the middle.

---

### Post by plucky on 2014-07-15
You can only move the front of a partition into un-allocated space,but you can resize the rear of a partition into un-allocated space.

i.e the un-allocated space has to be at the rear of the partition you want to resize.

Your goal would be to move the un-allocated space to the rear of sda8.

It has to be done in order.

1) Boot a Live DVD/USB.
    1a) Run Gparted
2) Make sure the swap partitions are dismounted. The Live DVD/USB will mount your swap partitions (Why do you have two swap partitions?)
3) Resize the extended partition so the un-allocated space is inside the extended partition. (you cannot resize the extended partition unless all partitions inside are dismounted and swap turned off)
4) Move all partitions within the extended partition to the left. (this will take a long time)
5) The un-allocated space should now be to the rear of /dev/sda8.
6) Resize /dev/sda8

Because you are moving all the partitions,the data inside the partitions also has to be moved.(This will take a long time.)

**OR**

From your setup,I would reduce the size of the / partition (/dev/sda6) to 15Gb and delete /dev/sda7 (swap) and that should give you 30GB of space between sda6 and sda8.

You can them move the start of sda8 into the un-allocated space created (this will take a long time) and you should then be able to resize sda8 after the move to encompass the un-allocated space which should now be at the rear of sda8.

If you delete the swap partition,you will have to reconfigure your system to mount the other swap partition.

Always backup your data before any partition reconfiguration just in case anything goes wrong.

Do you have a triple boot situation? As you have two swap partitions I assume you have two linux distributions installed.(I could be wrong)

Hope this makes sense.

Good Luck

---

### Post by Impavidus on 2014-07-15
You could boot from a live disk, turn swap off and the expand sda4 to the left. Then, after another, move sda9, sda10, sda11, sda12, sda5, sda6, sda7 to the left and finally expand sda8 to the left, which is an awful lot of work with many things that can go wrong just to get a little bit of breathing room in sda8. So it would be better to try and find other solutions. (Expand to the left is the same as move to the left, then expand to the right. I think gparted allows you to request a left-expand as a shortcut.)

There is quite some space left in sda6, which seems to be a root partition of a Linux install with a separate /home partition. It can be made smaller and then you can move sda7 to the left and expand sda8. Or you may be able to delete one of the swap partitions, as you usually don't need two of them (you have to update your fstab if you do so). It seems you're triple booting Windows and two Linux installs. You may be able to do something with sda12, which seems to me the /home partition of your other Linux system and is largely empty.

---

### Post by monkeybrain20122 on 2014-07-15
clone all the Ubuntu partitions with fsarchiver, then boot from a live usb and use gparted to wipe all the Ubuntu partitions, create new ones in the layout that you want, then restore the clones. Then fix the swap by editing /etc/fstab. This is a lot faster and safer than trying to move around/resize so many partitions with gparted.

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)
P.S. If you have uefi and use gpt then this won't work.

---

### Post by filipluch on 2014-07-15
Yes, I do have 2 Linux systems and one windows. I think that [[COLOR=#000000]plucky[/COLOR]]("http://ubuntuforums.org/member.php?u=317619")[COLOR=#000000] [/COLOR]'s idea was good, especially the second method is the best choice for me I Guess. I just didn't get the idea with un-allocated spaces before, that they should be near the partition you want to expand. Now I got it. Thank you.

---

