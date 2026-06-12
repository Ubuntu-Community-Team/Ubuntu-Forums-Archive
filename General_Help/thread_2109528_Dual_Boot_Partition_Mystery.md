---
title: "Dual Boot Partition Mystery"
date: 2013-01-27
forum: General Help
---

### Post by BEEDO on 2013-01-27
Hi,

I decided to put ubuntu studio 12.04 alongside XP pro on an  old laptop with a 250 GB hard drive for a dual boot. Being new to  partitioning and mounting, etc, I used Gparted to shrink XP from:

/dev/ntfs 232.88 GB      used 49.68 GB     unused 183.20 GB  unallocated 10.34 GB  to;

/dev/sda1 78.13 GB  (I was shooting for around 80 GB). 

next I installed with ubuntu studio cd and chose "something else" for the type of installation
my installation type table ended up like this: (I am rounding my GB's)

/dev/sda1     ntfs                               84GB     (did not check the format box)     I didn't select a mount point
/dev/sda2     EX4       /                      25GB      (checked format box)
/dev/sda4     EX4      /home           136GB      (checked format box)     This was the left over space after I did the others
/dev/sda3     swap                               5GB      (checked format box)      I put this at the "end" of  the volume

So,  I started up XP and all my programs and files worked like before, then I  rebooted to ubuntu and it worked as expected, but there was an extra  desktop icon labeled "84 GB File system" that when moused over says  'removable volume not mounted yet'
 It is a copy of what I have in my  XP partition or else it is what is in the partition. Should I assign it  a mount point and if so where? or perhaps something else?

Can anyone help? Thanks!

---

### Post by HiImTye on 2013-01-27
that's your ntfs partition. I would stay away from mounting and writing to it, but you can mount it for copying from it if you need to.

---

### Post by Bucky Ball on 2013-01-27
It is /dev/sda1, the Windows partition I presume. If you want to create a mount point so it mounts at boot you can or you should be able to just click on it. 

It is not a copy, it is the actual partition and the real contents. You can read and write to it without issue (or should be able to). If not there is software that can help. 

One issue you have is if you want to share data between Win and Ubuntu, Ubuntu can access NTFS partitions but Windows will not recognise EXT* partitions. You might want to create an NTFS partition for sharing data between the two if this is a requirement.

---

### Post by BEEDO on 2013-01-28
I agree that it is my xp partition. I would like to remove the icon on the desktop but I am not sure how to do it. I have removed the default icons (home, trash, file system) in the past without trouble, but I don't like risking the xp os since I don't have an installation disc. Also I don't know how to get rid of the icon other than deleting it.
 

 I found a web page that suggested I should have mounted it to /mnt/win_C by editing the partition during installation:
 

 [http://]("http://linuxconfig.org/how-to-dual-boot-windows-xp-and-ubuntu-linux")[linuxconfig.org/how-to-dual-boot-windows-xp-and-ubuntu-linux ]("http://linuxconfig.org/how-to-dual-boot-windows-xp-and-ubuntu-linux") 6.2 &#8211; 6.3
 

 I am sure I could do that now in terminal, but I am not sure how to return it to where it is if I don't like the results.
 

 So to be clear: I want my dual boot to work (like it does now) without risking it and I want to remove the icon without mounting it in sda2,3, or 4.
 

 I look forward to some insight!
 

 (Good idea about adding a (logical ?) partition for ntfs for file sharing. I will have to do that after I get this sorted)
  ;)

---

### Post by Impavidus on 2013-01-28
You could put your windows partition in /mnt/win_C now. First create the (empty) directory. Type in a terminal **sudo mkdir /mnt/win_C** or use a graphical file manager with gksudo. Next make a backup of your /etc/fstab and open it for editing:```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```Then add the following line```

/dev/sda1 /mnt/win_C ntfs defaults 0 0
```Instead of defaults you can use other options, see **man fstab** for details. This should mount your windows partition on /mnt/win_C and remove the icon.

If you want a shared data partition (saver, as you can no longer damage the windows system from linux) you'll have to replace one of your primary partitions (I suggest /dev/sda4) by an extended partition and recreate in that partition your /home and your shared data partition.

Edit: I may have to add that the web page you found seems a bit old. It's about installing Ubuntu 8.04 and suggests using FAT32 for the shared partition. No need to do so now, as Linux can read and write ntfs.

---

### Post by coffeecat on 2013-01-28
> **BEEDO said:**
> I don't like risking the xp os since I don't have an installation disc.

You may be interested in one or the other set of mount options for /etc/fstab mentioned in this Ubuntu wiki page:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Go down to the "Configuring /etc/fstab" - "Manual Configuration" section and then scroll down to the "Two special cases" part. One gives you read-only access which is what I would prefer for a Windows C: partition. The other disables graphical mounting and the "84 GB File system" entry *should* disappear from the file manager - but I don't know what will happen with the desktop icon.

Another tip - if you want to go for the former and have "84 GB File system" replaced by something more informative, add a partition label for your Windows C: partition. You can do this with Gparted but probably better is by using Windows' Explorer in My Computer. Iirc you simply right-click on your C: partition and choose "rename". Next time you boot into Ubuntu Studio, you should see your partition label in the file manager.

---

### Post by BEEDO on 2013-01-29
Impavidus  - I followed your advice, mostly, and achieved the desired result. I am not as good as I'd like to be but try to improve every day, so  when I arrived at the 'gksudo gedit...' part I used 'sudo nano...' instead. I am more comfortable with vim, but I used nano once before and it was easy to add the line to the fstab file. I followed along fairly well until I got to the fstab part which like gksudo, I am not sure what it actually does. So thanks and I will spend some time trying to understand them and figure out how to follow your advice about the shared data partition.

Coffeecat - Thanks for the idea of making it read-only, the desktop icon is already gone.

So before I consider this thread concluded I will have to figure out how to make the windows partition read-only from the ubuntu side which doesn't seem like it will be difficult and modify my /home partition to contain a data sharing partition which actually does seem difficult to me at this moment...:-? (though I know it probably is not).

Any comments or pointers welcome! Thanks!

---

### Post by Impavidus on 2013-01-30
I always use vim but I noticed that most people are more comfortable with gedit. You can use any editor you like.

Instead of the "defaults" option you could use "auto,ro" or something like that to mount read-only. You may also want to set the windows partition as non-executable. Have a look at the manual pages for fstab and mount:```
man fstab
man mount
```If you want a separate data partition you'll need a fifth partition on your disk. Unfortunately you can only have four primary partitions and as you mentioned your partitions are known as /dev/sda1, /dev/sda2, /dev/sda3 and /dev/sda4 I know all of them are primary partitions. You either have to stop using a separate /home partition (putting your /home directory in the root partition) and reformat the current home partition as a shared data partition (change the mount point, move some space from the shared partition to the root partition), or format it as an extended partition (/dev/sda4) with two further partitions inside (/dev/sda5 as /home, /dev/sda6 as /mnt/windows_shared). Changing the home partition on an already installed system is possible using a live session, but slightly complicated. If you haven't done much yet with your Ubuntu system, you could consider simply reinstalling with the knowledge you have gained.

---

### Post by coffeecat on 2013-01-30
> **BEEDO said:**
> 
Coffeecat - Thanks for the idea of making it read-only, the desktop icon is already gone.

That sounds as though you used the "defaults,umask=222" fstab options in the wiki page that I linked. If you did, then.... 

> **BEEDO said:**
> 
So before I consider this thread concluded I will have to figure out how to make the windows partition read-only from the ubuntu side which doesn't seem like it will be difficult

You already have! :)

> **BEEDO said:**
>  and modify my /home partition to contain a data sharing partition which actually does seem difficult to me at this moment...:-? (though I know it probably is not).


According to the partition layout you posted earlier, you have created 4 primary partitions, which gives you no room for manoeuvre. You will need to replace one with an extended partition so that you can create a number of logical partitions. This is not particularly difficult if you are used to partitioning, but it's not trivial either.

---

### Post by oldfred on 2013-01-30
There is  a tool that can convert primary partition(s) to logical in an extended. Then you may be able to resize /home and add another partition. If mounting partitions with UUIDs they should not change, but if by device then it will. So best to be prepared to edit fstab or reinstall grub if attempting this change. Also good backups, just in case.

But you have to follow rules on partitioning like all logicals must be in one & only one extended partition.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by BEEDO on 2013-01-30
> Originally Posted by Coffeecat:
 According to the partition layout you posted earlier, you have created 4  primary partitions, which gives you no room for manoeuvre. You will  need to replace one with an extended partition so that you can create a  number of logical partitions. This is not particularly difficult if you  are used to partitioning, but it's not trivial either.     >  Originally Posted by Impavidus:
Changing the home partition on an already installed system is possible using a live session, but slightly complicated.Maybe I could (after backing up my partition table) copy /home to / under another name; shrink my / partition to have some unallocated space ahead of sda4

> Originally Posted by oldfred:
To convert a partition from primary to logical, at least one free  (unallocated) sector must exist between the partition and the one that  precedes it.Then I could delete sda4, and create sda5 formatted in EX4, and sda6  /mnt/win_shared formatted in ntfs. Next I could rename my /home and somehow move it into sda5, maybe using UUID's and fstab.

I thought I could use gparted and maybe Fixparts. I am not sure if this is a viable plan, but it is at least slightly complicated!

Before I do that I thought I'd wait and see if anyone can suggest a better way...:o

---

### Post by oldfred on 2013-01-30
I think when you run fixparts it automatically creates the extended which then includes the logical(s) you have changed.
I do not know if you have to have one primary available first or if it will work with all 4 used.
A couple of users have posted that it does work. You can load it and have it analyze your partitions without having to change. Only if you write the changes will it update the partition table.

Just about all the other choice require deleting a partition usually swap is easiest and create the extended, then you can shrink /home, move extended to include unallocated and create logical partitions including  a new swap. And then update fstab with new UUID for swap.

---

### Post by BEEDO on 2013-01-31
I think I am getting close to the end of the trail with this thread, which seems to have wandered in a big circle.

I backed up my partition table with sfdisk, installed Fixparts and ran it. Despite the fact I had no unallocated space, the partition table that Fixparts displayed indicated that I could change my primary partition containing the swap space into an extended one, which I did and now contains the logical partition that is used for the swap space.

Then with gparted I shrunk my /home partition and then expanded the extended partition into the vacated space and added another logical partition formatted with ntfs. I named it 'shared' and it appears on my desktop as an icon now.  

And by going to the settings manager and from there to 'desktop', clicking the icons tab there is a box under 'default icons' that if I uncheck will remove "removable icons" which is where '84 GB file system' used to be and now is occupied by 'share'. Which is an answer to part of my original question of how to get rid of the icon.

This time however, instead of moving my xp system files into an area of relative safety, I want an accessible place to put shared data. It seems like it would be good in /home/beedo so I made a directory /home/beedo/share and made a /etc/fstab entry: /dev/sda6 /home/beedo/share ntfs defaults,rw (the rw is just a guess).

Anyway, 'shared' won't mount  and displays an error that says only root can mount 'shared'. When I look at it in xp it is called drive :E. My 'shared' file under beedo is apparently just an empty file.

So now I suppose my question is 'where is a good accessible place for 'shared' ?

And my fstab is looking pretty hokey, so I still have to figure that out. 

Thanks for all the helpful input! I'll get there  yet!

(helpful input still welcome! ;))

---

### Post by coffeecat on 2013-01-31
> **BEEDO said:**
> 
This time however, instead of moving my xp system files into an area of relative safety, I want an accessible place to put shared data. It seems like it would be good in /home/beedo so I made a directory /home/beedo/share and made a /etc/fstab entry: /dev/sda6 /home/beedo/share ntfs defaults,rw (the rw is just a guess).

Anyway, 'shared' won't mount  and displays an error that says only root can mount 'shared'. When I look at it in xp it is called drive :E. My 'shared' file under beedo is apparently just an empty file.

So now I suppose my question is 'where is a good accessible place for 'shared' ?

And my fstab is looking pretty hokey, so I still have to figure that out. 

First thing - have another look at the wiki page I linked in an earlier post. In fact, it would be useful if you read it through. It gives you a good, usable fstab line for general-purpose NTFS read-write. The options "defaults,windows_names,locale=en_US.utf8" are there for a purpose.

Next - you'd be better using /media/shared (or whatever you like in /media) as a mountpoint. Using the above options from the wiki, you shouldn't get an error. If you want a folder in your home that leads to your mounted NTFS shared folder, you need only then create a symlink.

Create a mountpoint in /media (I'll use /media/shared as illustration), and edit your sda6 fstab line with that and with the wiki mount options. Unmount and remount sda6 from the terminal, or simply reboot. Then delete your /home/beedo/share folder, and to create a symlink called shared in your home folder:

```
ln -s /media/shared /home/beedo/shared
```

---

### Post by BEEDO on 2013-02-01
>                      Originally Posted by **BEEDO**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12484140#post12484140")                 
                 [I]This time however, instead of moving  my xp system files into an area of relative safety, I want an accessible  place to put shared data. It seems like it would be good in /home/beedo  so I made a directory /home/beedo/share and made a /etc/fstab entry:  /dev/sda6 /home/beedo/share ntfs defaults,rw (the rw is just a guess).

Anyway, 'shared' won't mount  and displays an error that says only root  can mount 'shared'. When I look at it in xp it is called drive :E. My  'shared' file under beedo is apparently just an empty file.

So now I suppose my question is 'where is a good accessible place for 'shared' ?

And my fstab is looking pretty hokey, so I still have to figure that out.[/I]
It was late when I wrote that and I hadn't rebooted so when I did, today,  the icon was gone and /home/beedo/share existed and was read/write. I then reread the wiki page suggested by Coffeecat and the fstab man page and found my entry acceptable, just not "robust". Twixt the two pages, I was able to achieve greater understanding of fstab and now am able to write "robust" entries. The 'sudo blkid' command is especially useful as it gives all  the UUIDs!

Thanks to everyone that helped me, for your time, knowledge, and patience! :P

---

