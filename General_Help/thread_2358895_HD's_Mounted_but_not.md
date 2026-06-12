---
title: "HD's Mounted but not ?"
date: 2017-04-18
forum: General Help
---

### Post by scriber on 2017-04-18
Not a big deal as I go to files on first boot and click on each of the 4 HD's to manually mount each one, then the up arrow thingy on the right of each HD appears and it is mounted.

I'm confused as when I check each HD in Disks, it shows that Automatic Mount is on, and there is also a checkmark besides Mount Options.

Reason I'm asking is, if I forget to physically click on each HD before running Steam, then Steam doesn't find my game files on one of those HD's and I have to exit Steam and mount the HD first.

I'm fairly new to Ubunu so I'm not sure where to go from here.

---

### Post by Impavidus on 2017-04-18
The normal way to automatically mount your hard drive partitions is by using fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You can use fstab to mount the partitions wherever you want (although it's not a good idea to mount them some place where other files are located), but it's recommended  to put them at /mnt/data or something like that. So that's different from where they are mounted when you simply click in the file manager. You may have to reconfigure steam. I don't use steam myself.

---

### Post by scriber on 2017-04-18
Thanks for the reply, much appreciated !

When I type /etc/fstab in a terminal window, I get Permission denied.

Not sure I even want to go there anyway as I use BIBM ( [http://www.terabyteunlimited.com/bootit-bare-metal.htm](http://www.terabyteunlimited.com/bootit-bare-metal.htm)  ) for a boot manager, as I have 9 Primary partitions for different OS's on my first HD, and I don't want to screw anything up, even though I have everything backed up and can restore in a few minutes if need be.

I was curious to know what the fstab file shows, but if I don't know how to show it, I guess I should leave it alone anyway :-)

---

### Post by Bashing-om on 2017-04-18
scriber; Hello;

> 
I was curious to know what the fstab file shows, but if I don't know how to show it, 


One can "look" by several means - from terminal:
```

cat /etc/fstab

```
And to edit (add to ) the file one uses a text editor ( for unity is gedit for the GUI app ):
```

sudo -H gedit /etc/fstab

```
But, make sure you know what you are doing prior to the edits AND make a backup of the current file before beginning the edit operation.

Then test that the file is acceptable after the edits:
```

mount -a 

```

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by scriber on 2017-04-18
Thanks so much for that, I learn a little more each day :cool:

So after getting this :

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=98b036be-3fbd-43dc-bea0-30ba3f7abb5b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=14d1c21c-dffe-4aba-b53a-01d4d0ba9409 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

It appears that my 4 HD's aren't being mounted, even though the Disks app says they are.

I can live with that for now, not really a problem, I will tackle that later now I know where I'm at.

---

### Post by Bashing-om on 2017-04-18
scriber; Hey;

Any day I do not learn something more about ubuntu - I am disappointed ! 

Let me see what I can do to teach about what is going on with mounting:
OK; GUI has it's means to mount that is a layer on top of the kernel, gvfs .
to see all devices available for mounting/or mounted :
```

gvfs-mount --list
```
and an explanation of what this is :

in terminal execute:
```

man gvfs

```

Keep in mind " layer on top of the kernel" . Going deeper into the system and this lower level is a means to interface directly .
Now that is the function of the /etc/fstab file . Tell the kernel what you want mounted and exactly how, what, when and where !
fstab tutorial:[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <- bodhi.zazen -Understanding fstab
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336) <-Manualy edit fstab - why(Morbius1)

These say it better than I can .

[INDENT][INDENT]you too can be the master of your machine
[/INDENT][/INDENT]

---

### Post by scriber on 2017-04-19
Thanks again for the reply Bashing-om :cool:

After running this :

```
gvfs-mount --list
```

I get :
```
Drive(0): ST1000DM003-1ER162
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
Drive(1): ST3000DM001-1ER166
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
  Volume(0): Data3
    Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
Drive(2): ST3320620AS
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
  Volume(0): Game Data
    Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
Drive(3): ST3160815AS
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
  Volume(0): Data 2
    Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
Drive(4): ST2000DM001-1CH164
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
  Volume(0): Games2
    Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
Drive(5): Floppy Drive
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
  Volume(0): Floppy Disk
    Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
Drive(6): ASUS    DRW-24B3LT
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
Drive(7): HL-DT-ST DVDRAM GSA-4040B
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
Drive(8): Verbatim STORE N GO
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
  Volume(0): STORE N GO
    Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
    Mount(0): STORE N GO -> file:///media/logman/STORE%20N%20GO
      Type: GProxyMount (GProxyVolumeMonitorUDisks2)
```

and ```

sudo blkid 
```

I get this :

```
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/sda1: UUID="98b036be-3fbd-43dc-bea0-30ba3f7abb5b" TYPE="ext4" PTTYPE="dos" PARTUUID="6f875cd6-01"
/dev/sda2: UUID="14d1c21c-dffe-4aba-b53a-01d4d0ba9409" TYPE="swap" PARTUUID="6f875cd6-02"
/dev/sdb2: LABEL="Data3" UUID="21B78EF713C2C8B5" TYPE="ntfs" PARTUUID="0e55aefb-3958-4986-9ca6-cdfacf4b6128"
/dev/sdc1: LABEL="Game Data" UUID="9644389844387D55" TYPE="ntfs" PARTUUID="ed96ed96-01"
/dev/sdd1: LABEL="Data 2" UUID="BC60309860305B7A" TYPE="ntfs" PARTUUID="1903c4b9-01"
/dev/sde1: LABEL="Games2" UUID="CE3C2B0E3C2AF0DF" TYPE="ntfs" PARTUUID="942493ea-01"
/dev/sdf1: LABEL="STORE N GO" UUID="97E5-9723" TYPE="vfat" PARTUUID="c3072e18-01"
/dev/sdb1: PARTUUID="1741603d-f5ec-4efc-9130-6d15b3ac01f1" 
```

I did a quick read of ```


man gvfs


```

and I think I would have to spend more time than I have available right now to figure this out.

I'm not even sure how to backup fstab right now, but then if I did make a mistake, it would only take a minute to reinstall the Ubuntu Partition from an image.

All 4 of those HD's, Game Data, Games 2, Data 2 and Data 3 are used in 4 Windows OS's, I can access all 4 HD's from all OS's including Ubuntu, and Data 3 is the one I also use for both Windows and Ubuntu ( Steam ).

So I would really have to know what I'm doing so I don't make a mistake.

Like I've said, I can live with the way it is right now, I just have to make sure I mount Data 3 before running Steam.

Thanks again for all the info you've provided, I do appreciate it, and I'm sure I'll figure it out from the leads you have provided !!

Btw, I am the Master of the complicated setup of this machine, but certainly am a neophite when it comes to Ubuntu. :smile:

---

### Post by yetimon_64 on 2017-04-19
> **scriber said:**
> ...I'm not even sure how to backup fstab right now, but then if I did make a mistake, it would only take a minute to reinstall the Ubuntu Partition from an image....
Rather than having to reinstall a complete system to recover the /etc/fstab file should you make a mistake, open a terminal and issue the next command ...
```
sudo cp /etc/fstab /etc/fstab.orig
```
This will create an exact copy of your current file and store it in the file /etc/fstab.orig. 
This backup (.orig) file can be used to recover the file in a few seconds rather than reinstalling from an image which, depending on when it was made, can cause your current set up to lose installed applications or any other changes you have made to the system since the backup was made.

To restore the original /etc/fstab the command would just be the same as above with the files changed around, takes a couple of seconds with the terminal, for example to restore the original file ...
```
sudo cp /etc/fstab.orig /etc/fstab
```
Notice how the 2 files have just been swapped around.

For the specific entry I'll leave bashing-om or other helpers to help you generate the needed entry for the data3 drive as I am not too sure of what options you will need with your ntfs file system and set up. Good luck, yeti.

---

### Post by scriber on 2017-04-19
Thank you so much for the helpful reply,  yetimon_64

When I was talking about making /restoring an image, it takes less than 4 mins for the Ubuntu partiition, it's tiny, around 8.5 GB, compared to my Win7 one of around 40 GB.

Now I know how to backup the fstab file, I guess that will be simpler, thank you.

All these commands for the Terminal are bringing back memories of my MS-Dos days, before Windows :)

---

### Post by yetimon_64 on 2017-04-19
> **scriber said:**
> ....When I was talking about making /restoring an image, it takes less than 4 mins for the Ubuntu partiition, it's tiny, around 8.5 GB, compared to my Win7 one of around 40 GB.
Yes, I am aware how quick using an image is, I was in the habit of using them for a while.
Problems can arise with using images that do not include any recent program installations or system configuration changes since the time the image was made. If you make regular images that is not such a big problem, but as the image ages system changes can vary significantly to the original image.

> **scriber said:**
> ...Now I know how to backup the fstab file, I guess that will be simpler, thank you.... And safer for your newer system settings and applications etc ... you're welcome, cheers yeti.

---

