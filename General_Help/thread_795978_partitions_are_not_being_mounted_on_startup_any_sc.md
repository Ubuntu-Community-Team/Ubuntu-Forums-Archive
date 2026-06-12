---
title: "partitions are not being mounted on startup: any script to fix this?"
date: 2008-05-16
forum: General Help
---

### Post by hurinth on 2008-05-16
hello, suddenly my partitions are not being mounted as in other clean installations

I have a boot only disk, and another hard disk dedicated to storage

The boot disk has 3 partitions, one with windows, one is empty and sda2 is my ubuntu boot. (hardy heron)

How ever, I don't recall when exactly, the data-only disk and the XP partition are not being mounted automatically at startup, thus, producing crashes with applications like Rhythmbox which takes the music collection from my data disk

The weird thing is, if I insert a DVD-RAM I am able to see it mounted automatically. Any idea is welcome here

---

### Post by hermes0710 on 2008-05-16
There is a configuration file "/etc/fstab" which actually "says" to the system what to mount and where? You must provide us with more information in order to help you. The XP partition is fat or ntfs? What about the storage disk too? Is there only one partition in it?

---

### Post by EXCiD3 on 2008-05-16
Also if you failed to shutoff your computer normally, NTFS partitions will complain and refuse to mount until they are "safely removed" from a windows installation. Sometimes this is the case and causes automounting to fail also.

---

### Post by Gina on 2008-05-16
This happened during the very last stages of Hardy development - the beta was fine and several updates afterwards but between then and the final release something went wrong and we no longer seem to have partitions auto-mounted at boot even with the auto-mount option turned on.  I hope they can fix this before the 8.04.1 release - it's a **very bad failing IMO**.  OK so we more knowledgeable people can fix it by messing with fstab but it's **not good for newbies.**

---

### Post by hurinth on 2008-05-18
This is sad Gina, cant believe we are moving backwards instead of forward... Now I have a bigger problem: 

I reinstalled the OS yesterday (yes, again...) and found that indeed, no matter how fresh the installation is, the partitions won't be mounted automatically. So I messed a lil bit with the fstab that Hermes told me, however I am not sure how to edit this file and have the partitions mounted automatically. 

Right now the big issue is that I wrote "auto" as a Mount Option for my storage partition, which, to answer Hermes question, is a physical volume with only 1 logical volume (one partition one disk drive) I went to Computer>MEDUSELD>dob click to mount>right clic>Volume tab>Settings and I wrote "auto" in the Mount Options: text field. I left Mount Point blank and File system blank.

If I try to mount that disk again I get the error in the screenshot. 

Ne help will be greatly appreciated

---

### Post by EXCiD3 on 2008-05-18
Here is a really good article on understanding the fstab: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Adding an entry for the partition in the fstab will allow ubuntu to automount when it starts up provided it doesnt have any trouble mounting it.

You probably need to specify a mount point for your partition. You should just create a directory in /media for it (simple "sudo mkdir /media/<folder name>" in terminal can do that. Put the "/media/<folder name>" in as the mount point and then try it again. You should probably fill out as much info on that tab as you can. Ubuntu will probably try to guess where you want it mounted and the file system type, but im not sure so its always best to specify.

---

### Post by hurinth on 2008-05-18
Right, the funny thing is that now I can't mount the volume, hence, I cant get the Volume tab to fill that information again....

Im gonna try doing it from fstab as soon as I understand it, what I fear is, that now that I have given the "auto" value to that disk, the fstab won't help much from now on.... I hope it does

---

### Post by hurinth on 2008-05-18
> **EXCiD3 said:**
> Here is a really good article on understanding the fstab: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Adding an entry for the partition in the fstab will allow ubuntu to automount when it starts up provided it doesnt have any trouble mounting it.

[COLOR="Olive"][B]Very nice document man! Im now able to mount it terminal-ish and then I erased the info on the Volume Tab... gotta spend some more time figuring out how to set the disk in automount, since Hardy Heron lost that feature.

Thanks a lot

PS: So I mounted the disk: > sudo mount /dev/drive /media/DRIVEDIRECTORY and it mounted nice and easy[/B][/COLOR]

---

### Post by EXCiD3 on 2008-05-18
No problem! Here is an example of an fstab entry that should work for automounting:

```
 /dev/sda1 /media/TEST-ZONE ext3	defaults       0	0
```

Just replace /dev/sda1 with the correct drive location in /dev. (This also assumes its in ext3 format as you should be able to tell from glancing at it.)

---

