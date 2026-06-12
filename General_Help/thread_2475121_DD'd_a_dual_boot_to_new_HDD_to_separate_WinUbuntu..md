---
title: "DD'd a dual boot to new HDD to separate Win/Ubuntu. GRUB points to new HD. Why?"
date: 2022-05-17
forum: General Help
---

### Post by 777funk on 2022-05-17
I was hoping to have the factory drive for win 10 and the new drive for Ubuntu (was originally on one drive) so I DD copied the stock drive to a new drive. The plan was then to delete win10 partitions from the new drive and (from Windows) delete Ubuntu from the original dual boot drive.  

I booted Windows once before deleting it from the new drive and strangely now Windows is loading from the copy (drive #2) and not the original drive. Why would GRUB change to look at the new HD for windows when the original is still intact? I've already deleted Ubuntu from the win drive and windows from the ubuntu drive (where it's for some reason wanting to boot from) and now Windows isn't working (of course). It's still there on the old drive but GRUB tells it to look at the new drive (where it is no longer present).

Is there a better way to do what I was trying to do with the dual boot? Is there a way to get the grub to point back to the old drive when windows is chosen from its boot menu?

---

### Post by yancek on 2022-05-17
If you want to dual boot and keep the systems separate, the best way to do that is to install one OS and before installing the second OS, disconnect the original drive.

Are both Ubuntu and windows UEFI installs?  The problem with the way you did it is that now you have 2 identical systems on 2 different hard drives, with the same device/partitions and UUID'S. If you wanted Ubuntu and windows each on a separate drive, you would have been better off just moving Ubuntu to the 2nd drive.  Not sure why you copied or cloned both.  Do you have boot repari?  If not, get it at the site below and use the 2nd option described on the page and the Create BootInfo Summary selection and post the link you get when it finishes her.

---

### Post by HermanAB on 2022-05-18
As mentioned above, if you clone a disk, then you got to refresh the UUIDs to ensure that they are unique again, otherwise, the disks will be mounted 'on top of' each other and then you will only see one of the two.

---

### Post by 777funk on 2022-05-19
I do realize that it is a better idea to install on the separate drives  to begin with. I bought the second drive after the fact thus the desire  to move ubuntu post the new drive purchase.

So now it looks like I need to make sure the UUIDs are unique. I have no idea where to start with that.

---

### Post by dragonfly41 on 2022-05-20
Using Gparted might be a start

Refer here to section .. Changing a partition UUID

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

You can use Gparted on drives while in a LiveUSB session. "Try Ubuntu".

But experienced users might suggest an easier way through commands. I don't know.

I'm just interested since I am going through a juggling exercise right now, changing internal HDD (with Windows) to SSD (with new Windows).
But my Ubuntu partitions are all in external SSD's in a dual docking bay USB 3.0. I prefer to keep Windows and Ubuntu on different physical drives.

---

### Post by oldfred on 2022-05-20
Most find it quicker to just do a new install & restore from your normal backups.

It becomes a good test that your normal backup includes everything you need to restore system when a drive totally fails. And you have done process, so know you can recover. You also still have original install to find anything backup was missing.

One knowledgeable user posts (TheFu) that if it takes more than an hour to repair system a new install is quicker.
And new install & restore should not take more than an hour or you are not doing it right.

---

### Post by 777funk on 2022-05-20
> **oldfred said:**
> Most find it quicker to just do a new install & restore from your normal backups.

It becomes a good test that your normal backup includes everything you need to restore system when a drive totally fails. And you have done process, so know you can recover. You also still have original install to find anything backup was missing.

One knowledgeable user posts (TheFu) that if it takes more than an hour to repair system a new install is quicker.
And new install & restore should not take more than an hour or you are not doing it right.

This is very true. Actual hands on time is about 20 minutes on a new install. 

My predicament is trying to save Windows. The drive I cloned (as in the original with the dual boot) is untouched. I just can't get it to boot now. Not sure why other than the explanation with UUID which I assume to be correct.

---

### Post by dragonfly41 on 2022-05-20
Gparted will inform you if you have boot flags set on Windows partition.

I am about to swap out internal Windows 1TB HDD with a fresh 1TB SSD and then reinstall fresh Windows.

I intend to follow steps here ..

[https://answers.microsoft.com/en-us/windows/forum/all/clean-install-of-windows-10-os-on-new-ssd-best/9186ae98-b2b4-4b7a-b3ff-0b053ce2d1c9](https://answers.microsoft.com/en-us/windows/forum/all/clean-install-of-windows-10-os-on-new-ssd-best/9186ae98-b2b4-4b7a-b3ff-0b053ce2d1c9)

---

