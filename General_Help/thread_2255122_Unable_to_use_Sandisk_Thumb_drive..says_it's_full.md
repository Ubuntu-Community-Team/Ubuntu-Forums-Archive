---
title: "Unable to use Sandisk Thumb drive..says it's full"
date: 2014-12-02
forum: General Help
---

### Post by A.O._Stanley on 2014-12-02
32g thumb drive won't take any files because it says it's filled to capacity. I have a 2.2g file on the thumb drive but it won't take any more. When I go to Windows and look at the thumb drive it shows the 2.2g file and then shows 29g of free space.

I am trying to move files from Ubuntu to Windows with this thumb drive. How can get Ubuntu to recognize that the drive has plenty of space?

Thanks

---

### Post by Impavidus on 2014-12-02
Are you trying to move a large file? Most thumb drives are formatted FAT32, which has a limit of 4GiB file size. Any larger and it will report the disk is full.

---

### Post by A.O._Stanley on 2014-12-02
When I'm in Ubuntu and I click on 'properties,' it shows that there are 98 items on the drive and combined they take up most of the space. So I can't put anything else on the drive.

The files I am trying to load are in the 1-2gb range so the FAT32 limitations don't apply.

Thanks

---

### Post by mcduck on 2014-12-02
check for any hidden files (press Ctrl-H to show them in file manager) and try emptying trash bin (any deleted files are stored in hidden trash folders *on the device they were in the first place*, so if you've removed files from the drive and unplugged the drive without emptying the trash, the files are still there... Just emptying the trash should remove them, but if it doesn't just show the hidden files and delete them manually. (Shift+Del deletes files immediately without placing them in Trash, which can be useful for this...)

---

### Post by A.O._Stanley on 2014-12-02
> **mcduck said:**
> check for any hidden files (press Ctrl-H to show them in file manager) and try emptying trash bin (any deleted files are stored in hidden trash folders *on the device they were in the first place*, so if you've removed files from the drive and unplugged the drive without emptying the trash, the files are still there... Just emptying the trash should remove them, but if it doesn't just show the hidden files and delete them manually. (Shift+Del deletes files immediately without placing them in Trash, which can be useful for this...)

Thanks, I'll try this and see if it works.

---

### Post by A.O._Stanley on 2014-12-02
mcduck, nope. Still shows 98 files with 25gb of space used. I did find 4 files in the .trash so removed them but still don't have the space I should have.

Meanwhile, when I pop the thumb drive into Windows, I have nearly 32gb of free space for files. And, as I mentioned above, I am trying to move files from Ubuntu to Windows so not being able to access all the space on this thumb drive is making this difficult.

---

### Post by Impavidus on 2014-12-03
So the question is whether Ubuntu doesn't see all free space, Windows doesn't see all used space or something else is going on. What files does Ubuntu think are present on that usb drive? Try this in the terminal:```
du -ka /media/username/mountpoint
```Substitute your username and fill in the mountpoint. It's probably the only directory present there. This should list all files and directories present on that drive, along with their disk usage in kiB. Files are mentioned separately and included in the total of their directory.

---

### Post by A.O._Stanley on 2014-12-03
> **Impavidus said:**
> So the question is whether Ubuntu doesn't see all free space, Windows doesn't see all used space or something else is going on. What files does Ubuntu think are present on that usb drive? Try this in the terminal:```
du -ka /media/username/mountpoint
```Substitute your username and fill in the mountpoint. It's probably the only directory present there. This should list all files and directories present on that drive, along with their disk usage in kiB. Files are mentioned separately and included in the total of their directory.

Tried running that as you typed, but nothing happened and not sure where or what mountpoint is. However, after trying a couple of things I ran this:

```
du -ka /media/owsley/
```

That produced a lot of info and I'm not sure it's meaningful. Basically it listed every file I have in my video folder which would be way many gb's for the thumb drive to hold. 

From my novice point of view, it appears that the thumb drive has somehow associated itself with my video folder which would explain why under 'properties' it is showing that it contains 98 items and also that the drive is full. 

Any ideas on how to change this?

Also, I only have 52 items in my video folder so I don't know why 'properties' is showing 98.

---

### Post by yancek on 2014-12-03
> du -ka /media/username/mountpoint

If you don't know what the mount point is I don't see how you can be trying to copy anything to it.  It could be a UUID which if it is a FAT32 filesystem would usually be an 8 character combination of letters/numbers or it could be called Sandisk.  You need to replace 'mountpoint' in the command above with whatever you were trying to copy to on the flash.

---

### Post by A.O._Stanley on 2014-12-03
> **yancek said:**
> If you don't know what the mount point is I don't see how you can be trying to copy anything to it.  It could be a UUID which if it is a FAT32 filesystem would usually be an 8 character combination of letters/numbers or it could be called Sandisk.  You need to replace 'mountpoint' in the command above with whatever you were trying to copy to on the flash.

Yes, I see "1CDE-1595? and that is probably what you mean. Too late this time, though. 

In the meantime, I plugged the thumb drive into Windows and it showed only a few gb's of free space so I formatted it and that has solved the problem for now, but it is probably going to come back once I start filling the drive up again.

---

