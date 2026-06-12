---
title: "Moving, adjusting partitions"
date: 2007-06-13
forum: General Help
---

### Post by weblordpepe on 2007-06-13
Hi Guys.
I am seeing help with something that I want to do with my partitions. Basically the current arrangement is a mess, and I want to fix it all up and make it simple. Without reinstalling Ubuntu.

[IMG]http://homepages.slingshot.co.nz/~davoman6/gparted.png[/IMG]
At the dawn of time there was just Windows XP occupying the whole 60GB. I created a second partition for Ubuntu, as ya do. So far so simple.

Then I ran out of space for games. So I shrank the Windows Partition, and created two new partitions.

One NTFS, the other ext3 and mounted it to /usr/local


Now I have bits of free space all over the place and running out of room.

I want to basically do this:
**Keep Windows XP and Ubuntu's partitions**, and get rid of the rest.
**Move Ubuntu's partition so it is right after the XP partition.**
**Resize it to occupy the rest of the space on the disk, after XP**

I don't care about losing data on /usr/local or on the 20gb NTFS volume.

Where I am up to:
[IMG]http://homepages.slingshot.co.nz/~davoman6/gtparted-second.png[/IMG]
I have managed to (without confirming) get this far:
All ugly partitions removed, but I cannot move my main partition backwards due to it being mounted. It requires me to unmount / which I cannot do. How can I do this? 

Secondly
If I simply move my Ubuntu partition backwards and let it occupy all that free space, what will Grub do? Will the computer find Grub? Will I need to use the Ubuntu disc to reinstall Grub?

If I boot to the live CD, can I edit the partitions?

Thanks for your help guys in advance. Once I know I can do everything, I'll go ahead & bite the bullet.

---

### Post by jimbob on 2007-06-13
Download and burn the stand-alone bootable Gparted disk and you can do what you want:

[http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=umn&filename=gparted-livecd-0.3.4-7.iso&39546595](http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=umn&filename=gparted-livecd-0.3.4-7.iso&39546595)

Move that first partition sda1 to the far right into the unallocated space temporarily and then move your Ubuntu partition sda3 all the way to the left and then grow it as far as you want after putting sda1 into its final position.  Create a swap partition at the end = to or > than your memory size.

When you are all done adjust your /etc/fstab and /boot/grub/menu.lst to reflect the new partition names and you should be good to go.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by weblordpepe on 2007-06-13
> **jimbob said:**
> Download and burn the stand-alone bootable Gparted disk and you can do what you want:

[http://sourceforge.net/project/showf...kage_id=173828](http://sourceforge.net/project/showf...kage_id=173828)

Move that first partition sda1 to the far right into the unallocated space temporarily and then move your Ubuntu partition sda3 all the way to the left and then grow it as far as you want after putting sda1 into its final position.  Create a swap partition at the end = to or > than your memory size.

When you are all done adjust your /etc/fstab and /boot/grub/menu.lst to reflect the new partition names and you should be good to go.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

Hot dang. Thats A+ Linux support right there folks.
Thanks jimbob, lets see how I get on.

---

### Post by jimbob on 2007-06-13
For some reason that link didn't work.
 I corrected it in my post above.

---

### Post by weblordpepe on 2007-06-14
Damnit! It worked!! :guitar: :guitar: It took like an hour because I think I fumbled about. But cheeeeck it out!! 

[IMG]http://homepages.slingshot.co.nz/~davoman6/gparted-done.png[/IMG]
Those are some clean partitions right there.

Thanks jimbob, I just googled up that gparted live CD and it worked like a charm. 

I haven't tested out Windows XP yet to see if it still goes. It should, since I didn't move the partition. But anyway yeah Ubuntu plays nice. All I needed to do after I screwed around was set the Ubuntu partition's 'Boot' flag.

I now have loads of free space to reload all my games on and applications. Wee.

---

### Post by DonnieP on 2007-06-14
The gparted livecd is da bomb.  I just used it to double the size of my Ubuntu partition using space unallocated after shrinking a Vista partition.

---

### Post by weblordpepe on 2007-06-14
We should all have a gparted livecd party.

---

