---
title: "Automount XP in 8.04???"
date: 2008-04-25
forum: General Help
---

### Post by shearroller on 2008-04-25
Guys, I just got Ubuntu 8.04 installed and ran into a problem with how it handles the XP partition - it's no longer auto mounted upon login.  In an effort to have my XP partition auto mounted upon login the first place I looked was in /etc/fstab but the partition isn't even listed there!  So I need help in getting my XP partition to be auto mounted.

In an effort to allieve your curiosity as to why I need it to auto mount, I use Thunderbird as my email client in both Ubuntu and XP  and to save myself a lot of headaches trying to sync the Ubuntu T'bird up with it's brother in XP I set things up in Ubuntu so that the Ubuntu T'bird uses the XP T'bird's Mail folder via a link.  Doing it this way gives me all of my mail and folders plus all of the filters I've created.  I've been doing it this way for a couple of years now and it works great - until Hardy that is.  Hence I need help in getting XP to auto mount.  Thanks.

Mike

---

### Post by pro003 on 2008-04-25
Select from upper panel 'Places" than your XP/ntfs drive and you'll be asked for password, of course you can chose to remember that mount just for the session or permanently. 

that's how I did it...

---

### Post by shearroller on 2008-04-25
Thanks for your response... 

That is how I originally mounted my XP partition and I did select the 'permanent' option but it still doesn't mount the partition automatically.  I've been saying I want the partition to be auto-mounted 'at login' but maybe I should be saying 'at boot up'.  I have even had a look at the SYSTEM/ADMINISTRATION/AUTHORIZATIONS module and I did set the MOUNT FILESYSTEMS FROM INTERNAL DRIVES option with 'no constraints' all to no avail.

---

### Post by compacho on 2008-04-25
I have the same exact problem and have tried the same things Shearroller has tried. I too would love some help with this.

---

### Post by ubuntu-freak on 2008-04-25
Have you installed GParted and tried mounting it with that? 
 
Nathan

---

### Post by Victormd on 2008-04-25
I think this is a Hardy "feature." I have 2 NTFS partitions, one of which is a data partition that contains all my files, including firefox and thunderbird profiles. Since Hardy doesn't automatically mount my partitions, every time I open firefox or thunderbird, I get a msg saying that there is already an instance of firefox/thunderbird running and that I should close them before tryint to open a new one... the problem is that all my profiles are on the ntfs partition. As soon as I go to Places>My-Partition and the icon shows up on the desktop, firefox opens normally. This is a pain and I wonder if there is a way to automatically set hardy to mount NTFS partitions (so the icon will automatically show on the desktop).

---

### Post by pro003 on 2008-04-26
I had some luck with unmounting the usb drive with gparted, but as far as ntfs partitions are concerned I did some googleing and found out it has to do with these two files

/etc/fstab   

/etc/mtab


but I recommend you to be careful on these two, better do some research how to manipulate with them... and if I find out how to set auto mount of ntfs partitions;

fstab looks like this 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c2bb02ae-a46b-47ae-bab4-4a5eb9082277 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=d5804c5b-3345-4097-a2a6-cb477ae08098 /home           ext3    relatime        0       2
# /dev/sda4
UUID=923a5008-13fc-4857-9cfb-9a9ab566ec5d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by shearroller on 2008-04-26
pro003 said:

> ...I did some googleing and found out it has to do with these two files

/etc/fstab

/etc/mtab

As far as I can tell, Hardy doesn't use fstab for mounting NTFS partition - fstab was the very first place I looked to fix this 'problem'.  My NTFS partition IS listed in mtab tho' but I'm not too sure it the entry can be modified.  As I thought - I just unmounted my NTFS partition and it's entry in mtab is no longer there!  So, with Hardy, fstab doesn't control NTFS partitions.

What I have learned is that the app 'gnome-mount' is what does the mounting and probably the unmounting of at least the NTFS partitions.  I'm not familiar with this app so I guess I'll just keep looking and playing.  I do intend trying to add a line in fstab just to see if it will take control of things.  I'll let you all know what I learn.

As far as using qparted or gparted for unmounting NTFS partitions I found it best to just right-click on the desktop icon for that partition and select 'unmount'.  You can also add a 'disk mounter' applet to your panel for doing the mounting & unmounting.  Your choice...

Thanks for all of your replies guys!

Mike

---

### Post by shearroller on 2008-04-26
Success!!!

It looks like fstab will/does take over control of auto-mounting NTFS partitions on boot-up!  I added the following line to my /etc/fstab:

/dev/hda1      /media/*UrMountPoint*	 ntfs	    defaults,umask=007,gid=46	   0	1

After saving the file I rebooted (just to be sure) and my NTFS partition was mounted upon login.  I guess an old dawg can learn new tricks :)

Enjoy!

---

### Post by pro003 on 2008-04-26
shearoller, can you show me how does your fstab looks like now, I want to add this line to but just to be sure I won't mess things up ya know...

thanks:guitar:

---

### Post by shearroller on 2008-04-26
Sure!  Here it is:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=ce107f6f-fce5-4f05-91ea-be3d93a7ff5e /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda3
UUID=16f736bd-61f0-4d0e-9a42-0121d640f4f7 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
## Added the following line in an effort to auto-mount XP 04/26/2008...
/dev/hda1	/media/M500_C	ntfs	defaults,umask=007,gid=46	0	1
```

FYI - whenever I modify any script I first make a back-up copy of that script and then I add notations in the script as to what I'm trying to do with the mods.  I've been bitten way too many times not to follow this sequence!

I'm surprised it worked, that some other app didn't wrest control from /etc/fstab...  Sometimes we get lucky with Linux...

---

### Post by pro003 on 2008-04-26
IT'S ALIVE, IT'S ALIVE!

yap man, it worked... this was not a big deal at all... can't wait another challenge... 

thankz:guitar:

---

### Post by shearroller on 2008-04-26
Congrats!

It seems in Ubuntu, and in Linux in general, there is always a way around a problem.

Enjoy...

---

### Post by bsmanian on 2008-04-26
First unmount all Other Partitions.Install ntfs-config ntfs-3g if not already installed through Synaptic Package Manager and ntfs3g.Right click Applications/Edit Menus/SystemTools and Select NTFS Configuration Editor and Close it.Go to Applications/SystemTools/Configuration editor and Configure as per your requirement.Immediately the partitions you have chosen ill appear as icons on your Desktop.

---

### Post by compacho on 2008-04-26
Success!! Thank you so much bsmanian! I think all my setup problems are solved now :D

---

### Post by pro003 on 2008-04-26
thanks... a lot! I just installed the ntfs-config & ntfs-3g and I f***ed up my D:/ from my wife's Vista...

I uninstalled it and roll back backed up fstab, but still unable to mount d:/(_ntfs)

says am not privileged to mount the volume???!!!

---

### Post by pro003 on 2008-04-26
ok guys i got it... am kinda distracted with some motorcycle and police chase around my block....:popcorn:

---

### Post by Victormd on 2008-04-26
> **pro003 said:**
> thanks... a lot! I just installed the ntfs-config & ntfs-3g and I f***ed up my D:/ from my wife's Vista...

I uninstalled it and roll back backed up fstab, but still unable to mount d:/(_ntfs)

says am not privileged to mount the volume???!!!

You don't need to install ntfs-config or ntfs-3g to get it working.
Here are a few checks before you edit your fstab.
When you boot into ubuntu, even though you don't have your ntfs partitions on the desktop, they should be listed in the menu "Places". Simply click on it and it should show up on your desktop.

Now, if you want to leave the same mount point as the ubuntu default, browse to your media folder (or in the terminal type cd /media    then ls) and look at the mountpoint given to your ntfs partition (i.e. folder called backup - in my case).

Now from the terminal, type ```
sudo fdisk -l
``` this will list all your partitions. This is what my looks like.
> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4400    14860125   83  Linux
/dev/sda3            4401        4462      498015   82  Linux swap / Solaris
/dev/sda4            4463        9725    42275016    7  HPFS/NTFS


So from this list, I know I want to mount /dev/sda1 and /dev/sda4

Now, from the terminal type ```
sudo gedit /etc/fstab
```
this will open your fstab. Let's say I wanted to mount my /dev/sda1, then I would add this to the last line:
> /dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 1

This will mount /dev/sda1 in the /media/backup folder (as explained above)
simply keep adding lines as you need more partitions. Save your fstab and reboot. You should now get the partitions automatically mounted and the respective icons on your desktop

---

### Post by pro003 on 2008-04-27
Ok, I solved the problem, but I will anyway explain what happened.

1. Could not mount automatically NTFS at ubuntu startup
2. Solved the problem by editing /etc/fstab
3. Read post about installing ntfs-config & ntfs-3g
4. Screwed up line 2. by doing line 3.

Solution was to UNDO line 2. means delete the line I've added before, then started ntfs-config and ?I was automatically asked that there isn't mounted D:/ partition and do I want to mount it, then I've checked Yes... And there I go. Problem solved.

P.S. Even though problem was already solved by just simply editing fstab (line 2.), or look previous post above....

that's it:guitar:

---

### Post by cooltd825 on 2008-04-28
thanks!  this solved my problem too.

now i can listen to my music without having to manually mount it everything.

---

### Post by Victormd on 2008-04-30
An alternative to my previous post is to add a line to the end of fstab using the UUID option instead of /dev/sda1. You can determine the UUID by using (i.e., for sda1)
```
sudo vol_id -u /dev/sda1
```
so your fstab file will have this line
> UUID=NUMBER_ID /media/backup ntfs defaults,umask=007,gid=46 0 1
where NUMBER_ID is the output from vol_id for your device, i.e.:
UUID=78980E1B980DD890 /media/backup ntfs defaults,umask=007,gid=46 0 1
instead of
/dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 1
I found this to be more stable/suitable than using the ***/dev/sda1*** option

---

### Post by charonn0 on 2008-05-01
Thanks! It worked great!

---

### Post by rodrigo666 on 2008-05-14
Greetings,

I was having the same problem, but there's a script that solves it:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by walmis on 2008-05-18
My preferred automount method is to add *gnome-mount -d /dev/sda3 &* to startup programs. Using this you are still able to manage mounts via right click menu in nautilus (using fstab i get access denied when i try to unmount).

---

### Post by pro003 on 2008-05-18
since I have installed ntfs-config and ntfs-3g I don't find it any easier than this method... you just restart after install of ntfs-config log in to ubuntu don't mount manually ntfs partition i.e. don't click on them just go to applications > System or Other stuff and start ntfs-config - it will detect your ntfs drives and you just need to check those boxes to remember this action for next time and you're done... really easy

```

sudo apt-get update
sudo apt-get install ntfs-config ntfs-3g

```

cheers

---

### Post by Durd3n on 2008-05-26
I finally got this to work.  Here's what I was doing wrong and maybe this can help someone else:

In the NTFS Configuration Tool I wasn't checking 'Enable write support for internal device'

Also, I had to create the directory I wanted in /media

```

cd /media
sudo mkdir disk
```

I'm happy now.  Regards.

---

### Post by rodrigo666 on 2008-05-26
Still, the script I've posted above do the trick with no stress.

---

### Post by huczek on 2008-05-27
Bsmanian's post helped me. My NTFS partition mounts perfectly.

---

### Post by xen-uno on 2008-11-03
Rodrigo's script link worked perfectly on 8.10 x64. Thank button not appearing for some reason otherwise I'd give you your 1st. Will a wave work? ):P

---

