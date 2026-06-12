---
title: "can't install xubuntu"
date: 2007-04-22
forum: General Help
---

### Post by jexdawg13 on 2007-04-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				after upgrading to feisty, my ubuntu was slow to the point of being unusable.
i wanted to try xfce and xubuntu and see if the speed was worth the switch....

...except i can't make the switch.
i'm running the xubuntu livecd right now. when i try to install it, everything goes well until i get to the partition part of the process.

On the first partitioning screen (Prepare disk space), i choose:
```
 Guided - resize IDE1 master, partition #1 (hda1) and use freed space
```
i set it at 42%, or 30/.5 GB

next screen says: ```
 Before you can select a new partition size, any previous changes have to be written to disk.

You cannot undo this operation.

Please note that the resize operation may take a long time.

``` 
which is a standard message... whatever.

it checks the ext3 drive and whatnot, then tells me i'm a failure: 
```
The test of the file system with type ext3 in partition #1 of IDE1 master (hda) found uncorrected errors.

If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.
```
and then
```
An error occurred while writing the changes to the storage devices.


Then it brings me to the Prepare Partitions screen where I can do nothing.. if i hit forward, it says [code]No root file system is defined.

Please correct this from the partitioning menu.
The resize operation is aborted.
```


However, on the release notes, it says:
```

# On the Xubuntu desktop CD, installation may fail during partitioning with a warning such as "The ext3 file system creation in partition #1 of IDE1 slave (hdb) failed". Bug #107259. To workaround this, close the installer and follow the following steps:

   1. Go to Applications -> Settings -> Settings Manager.
   2. Select "File Manager".
   3. Switch to the "Advanced" tab.
   4. Click on the "Configure the management of removable drives and media ...".
   5. Uncheck both "Mount removable drives when hot-plugged" and "Mount removable media when inserted".
   6. Close all the windows just opened, and restart the installer.

```

I did all that and ran the installer again - another failed attempt, it changed nothing.

So I turn to you, ubuntanites.


I just want to install xubuntu. Make my dream come true.

Thanks :)

---

### Post by Cable on 2007-04-22
I would suggest that you download the alternate CD and try using that to install Xubuntu.  I have had the LiveCD from the past three releases act up on me, but the alternate CD's have never ever failed me.  Give the alternate CD a go and report your results here.

---

### Post by zazen666 on 2007-04-24
I had this same problem. After posting a few questions on the forums, I finally fiqured it out.
The Xubuntu partioner does not work so well I think. This is what I did.

I got a live disk called Gparted:
 [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

Which lets you partion your HD eaiser. I set one partion of about 1.5 for the linux swap, and the rest of the hd as ext3 (it means main HD for install, boot, etc)

Then I used Xubuntu live cd install. When I go to the partion (step 4), I selected manual. Xubuntu reconized the new partions. I set the ext3 to "root" with the symbol: 
"/"
Without quotes

That worked fine for me and now I have xubuntu up and running. I acutally like it better than ubuntu and it does seem faster on my computer with is about 3 yeras old.


Hope that helps.

---

### Post by Toshibi on 2007-04-29
There is a really easy fix for this and I had the same problem. It's much easier to:

1) Applications -> Settings -> Settings Manager
2) Click on the File Manager
3) Go to the Advanced Tab
4) Click on the Blue Configure Link
5) Uncheck the "Mount Removable Drives when hot-plugged"

Then attempt to install again. The problem is occurring if you have a SATA drive because it's remounting the drive before it gets partitioned causing an error.

---

