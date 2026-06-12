---
title: "How Do I Name A Hard Drive Or Rename One?"
date: 2014-11-25
forum: General Help
---

### Post by Smallwheels on 2014-11-25
I've got an external drive that I want to wipe and reformat using GPartEd. How do I name that drive and how can I rename other drives? I have some USB thumb drives and they all have their manufacturers names. That would be OK with just one but they all can't have the same name. I want to label them when they're plugged in so I can know which drive I need to select for specific files. 

Please let me know how to do this. If I need another program to do this then let me know which one. 

Thank you.

---

### Post by sammiev on 2014-11-25
You can use Gparted, you may have to make a bootable USB device with it as you would need to have your device you want to label unmounted.

---

### Post by Smallwheels on 2014-11-25
I'm sorry. I don't quite understand what you mean. I know how to open the program and arrange to wipe it and select the format. What do I click to insert a new name?

---

### Post by coldcritter64 on 2014-11-25
Once a partition is created in gparted (if it is mounted, it shows a "key", right click and select "unmount" to change, you need a partition unmounted to add or alter a volume label).

For the partition you want labeled right-click it and select "Label" from the context menu, set the name in the dialog box that pops up next. See screenshots.

Note in the screenshots, despite how the labels read, that is an installation on an external drive (/dev/sdc). The home labelled partition is mounted only for access to files on it from the install on /dev/sda (the one I am currently posting from).

---

### Post by Smallwheels on 2014-11-25
Thank you coldcritter64. The drive I'm altering will be a single 500 GB storage space. It will not be used for booting an OS. In the file window there are names of the external drives I have plugged in. If I just name one of the two partitions will that name show up in the file window?

---

### Post by coldcritter64 on 2014-11-25
That partition I am showing the label of in post 3, will show in the Nautilus file manager as "Linux-strg3" (even if unmounted). So to your question...
> If I just name one of the two partitions will that name show up in the file window? Yes, though you may need a restart/logout to set it fully, not sure for Ubuntu at the moment, I am on Debian.

 Check in the side pane of Nautilus as soon as you finish in and close gparted, the label may already be recognized and put in there.

If you have others unlabeled they will also show, but named by their size rather than by label. Your label should show in file managers for that partition.

---

### Post by Smallwheels on 2014-11-26
Using GPartEd I reformatted the drive. When done I clicked the drive name. There was just one partition listed so it was the only one to select. After doing that I started going through the drop down menus on the top of the window of the programs GUI. On one of them there was a choice called Label. I selected it and a small window opened with a box for me to type the name. I did that and when I completed the operation, the name of the drive that I had just given the single partition showed up in the drive list. 

I was able to rename it with the drive mounted. Mounting and unmounting is easy. Just look for the unmount choice in one of the drop down menus. It is just as easy to mount it. You just need to select the drive with the lock icon to unmount it.

---

