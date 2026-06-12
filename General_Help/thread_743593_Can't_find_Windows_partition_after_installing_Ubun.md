---
title: "Can't find Windows partition after installing Ubuntu"
date: 2008-04-02
forum: General Help
---

### Post by fearful on 2008-04-02
Hello I just installed Ubuntu 7.10 and I'm having troubles trying to find my windows partition. I have tried everything and searched all the forums!

I made the partition on the Ubuntu partition maker, made it 20gb and chose logical not primary. When I booted from the CD I was able to see the windows partition but now after it's completely installed I can't seem to find it. 

I get this when I use the fdisk function

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc22bc22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       17026       19457    19535040    5  Extended
/dev/sda5           17027       19457    19527007+  83  Linux

any help please?

---

### Post by ryanhaigh on 2008-04-02
Assuming you have only one drive it looks as though you have deleted your windows install. I may be wrong but fdisk should show you all partitions on a drive and as the only one on there is the Linux (ext3) it looks as though windows is gone.

---

### Post by fearful on 2008-04-02
Well than what should I do, I have a backup of my files on my external harddrive but its FAT32 so I can't mount it. Now since I have to keep Ubuntu as just one operating system, how do I recover my 120 GB of hard drive?

---

### Post by fearful on 2008-04-02
I'm kind of desperate to get back my 120 gb of hard drive to Ubuntu, and also I need to mount the FAT32 external I have finals and I really need to study lol:S

---

### Post by ibuclaw on 2008-04-02
What does your fstab file look like?

```
 nano /etc/fstab 
```

Was your Windows partition displayed when you loaded up the GRUB Bootloader for the first time?

Regards
Iain

---

### Post by fearful on 2008-04-02
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=452fc09f-57b7-4fe0-a5c8-592681595556 /               ext3    defaults,erro$
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



nope it doesn't show in the GRUB :\ and I'm sure I made the partition.

---

### Post by ibuclaw on 2008-04-02
Then it is long gone mate, sorry.

On the up side there are programs such as **testdisk** or **photorec**

you can get **testdisk/photorec** from the repository. it all comes as one package.
```
 sudo apt-get install testdisk 
```
Though **testdisk** is aimed at recovering lost partitions only.
And since you've done a complete swipe, the partition tables for windows may be long gone and unrecoverable.


**photorec** is your best friend then, as it aims at recovering any type of file from any formatted partition.
Type in:
```
 sudo photorec 
```
after installing and ring out whatever you can find.

Regards
Iain

---

### Post by fearful on 2008-04-02
well atleast maybe i can recover some stuff, well but how can i get my diskspace back to my ubuntu cuz i only got 15gb out of a 140gb hd :S

---

### Post by fearful on 2008-04-02
also the command for photorec says cannot be found :S

---

### Post by ryanhaigh on 2008-04-02
You should just be able to plug you external fat32 in and it should work ubuntu supports fat32. If you have a backup of everything you need then I wouldn't worry about trying to recover it will be a long and tedious process. There are also probably better tools for ntfs recovery if you do chose to go that way.

The command is not being found because you haven't got it installed. You can install via synaptic or using the apt-get command as for testdisk but be aware that every time you install something or do basically anything on your computer you are writing to the disk and reducing the chances of recovering files.

If you have your original windows disk you can always reinstall windows then ubuntu but probably best to leave this till after finals

---

### Post by ibuclaw on 2008-04-02
if you are getting this
```

The program 'photorec' is currently not installed.  You can install it by typing:
sudo apt-get install testdisk
bash: photorec: command not found

```
Then type in
```

sudo apt-get install testdisk

```

15GB hard drive?...

hmm, that is a bit odd. Maybe windows isn't gone afterall...
Maybe your BIOS settings need checking then... ?
Settings may not be fit for a dual partition (?)

I'm only guessing. It seems odd that a (large) section of your hard drive will just vanish.
check this just incase:
```

 o  Enter BIOS

 o  Make sure all HDD's are detected. 
     Take down notes of of the current settings for them,
     incase you have to restore them back later.

 o  Set your hard disk's MODE to AUTO
     (IF the setting says LBA, large, or normal, change it.)

 o  If you have this option available, set TYPE to USER,
     but don't change any of the figures that were automatically detected.

 o  Save the settings, and reboot.

```

Regards
Iain

---

### Post by Lord Illidan on 2008-04-02
I renamed your thread to be more specific to your problem, as Help Me isn't really indicative. Good luck!

---

### Post by fearful on 2008-04-02
Thank you, but no luck with the BIOS, I guess I'll just have to use Ubuntu as primary operating system, but I want to know how to get my 130gb back and how to use my FAT32 external HD

---

### Post by ryanhaigh on 2008-04-02
```
sudo apt-get install gparted
```
Or click this [apt:///gparted](apt://gparted)
This will install a partition editor which you will then be able to find under System>Admin and can use to make a partition from your unassigned 130GB. You will then need to add an entry to fstab which will depend on what filesystem you decide you use. If you are going to use windows as your primary os later than FAT32 if ubuntu then Ext3. Searching the forum should tell you how to add a partition to fstab.

What is happening when you plug in your external drive? If it does nothing then when you plug it in then run the command ```
dmesg | tail - 
``` and post it here (waiting a couple of seconds after plugging it in)

---

### Post by fearful on 2008-04-03
well it seems that there is nothing in the partition i deleted it i don't know why tho, and the problemm with the external hard drive fixed so its all good thanks :)

---

### Post by fearful on 2008-04-03
how can i merge the unallocated partition to my ext3 partition?

---

### Post by ryanhaigh on 2008-04-03
you can resize your current partition to take up the rest of the space. this will however effect the uuid of the partition and you will need to reconfigure grub and fstab (search forum for more info). I would suggest making the new partition separate and using it for your /home which is where all the user files are set. Keeping os and user files separate is always a good idea.

---

