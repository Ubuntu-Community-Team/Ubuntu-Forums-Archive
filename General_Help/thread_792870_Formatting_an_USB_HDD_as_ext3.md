---
title: "Formatting an USB HDD as ext3"
date: 2008-05-13
forum: General Help
---

### Post by Vashu on 2008-05-13
Is there a real benefit from doing this?
I just bought a 320gb portable drive. Since I don't use windows at home or my laptop didn't really feel like formatting NTFS was the best choice.

But since it is a portable hard drive after all being NTFS would mean windows computers would be able to read it easily. I was thinking of including the ext3 windows drivers in the HDD that windows computers would be able to read/write while still being able to use a Linux native format and being able to do disk checks and stuff.

Any thoughts on the matter?

---

### Post by maddog39 on 2008-05-13
Yes there is, ext3 doesn't get fragmented and you also don't run the risk of a rouge/buggy ntfs driver corrupting the whole drive.

---

### Post by bodhi.zazen on 2008-05-13
If you are going to use it with windows computer, I advise you leave it ntfs.

1. The linux ntfs drivers are , IMO, more reliable then the windows ext3 driver (fs-driver).

2. You can not install the Windows fs-driver if you do not have administrative access to the windows box.

---

### Post by Vashu on 2008-05-13
> **bodhi.zazen said:**
> If you are going to use it with windows computer, I advise you leave it ntfs.

1. The linux ntfs drivers are , IMO, more reliable then the windows ext3 driver (fs-driver).

2. You can not install the Windows fs-driver if you do not have administrative access to the windows box.
Really? I actually tought otherwise. My logic was NTFS is a closed format (filesystem?) while ext3 is opensource. It's easier to make a windows driver for a filesystem you know everything about than a linux driver for a filesystem you have to find out on your own thru trial and error.

---

### Post by bodhi.zazen on 2008-05-13
In theory you are correct, but it has not happened yet. the fs-driver, for example, does not recognize the journal and the ext3 is mounted as ext2 (ext3 is just ext2 with a journal).

You can look over these two links and decide for yourself :

[http://www.linuxquestions.org/questions/linux-general-1/are-you-successfully-using-fs-driver-for-ext3-519862/?]("http://www.linuxquestions.org/questions/linux-general-1/are-you-successfully-using-fs-driver-for-ext3-519862")

[http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)

---

### Post by timcredible on 2008-05-13
benefit of ext3 is that it retains file permissions, but it's not natively supported in windows

benefit of fat32 is that is natively supported by everything, but it doesn't retain file permissions.  

so, what should you do?  depends on what you're going to use it for.  i typically partition all my usb drives with both fat32 and ext3 (usually about 25% fat32, 75% ext3), that way i have both.

---

### Post by r76 on 2008-05-13
With fs-driver you will lose the journaling, so no advantage there.  FAT(16/32) will not handle large files >4GB (e.g. DVD iso and drive backup images) and has a max partition size in Windows of 32GB so not practical for your entire 320GB drive.

Ext3 will be great if file permissions are important to you, but I recommend NTFS - the drivers have long been mature for normal use (I run 3 NTFS 500GB disks on a daily basis with Ubuntu, and no problems), you get quicker unmounting, no problems with permissions if they are unimportant in your setup (an issue I always had previously when I used ext3).

As someone else pointed out, it depends though on what your usage requirements are

---

### Post by Vashu on 2008-05-13
> **r76 said:**
> With fs-driver you will lose the journaling, so no advantage there.  FAT(16/32) will not handle large files >4GB (e.g. DVD iso and drive backup images) and has a max partition size in Windows of 32GB so not practical for your entire 320GB drive.

Ext3 will be great if file permissions are important to you, but I recommend NTFS - the drivers have long been mature for normal use (I run 3 NTFS 500GB disks on a daily basis with Ubuntu, and no problems), you get quicker unmounting, no problems with permissions if they are unimportant in your setup (an issue I always had previously when I used ext3).

As someone else pointed out, it depends though on what your usage requirements are
My main usage for it is media storage. Movies and stuff. Permissions are irrelevant for me or more like unnecessary. 

What I'm more worried about is not being able to run disk checks and fix errors if they occur on NTFS. I move a lot (on foot regrettably) so bumping is bound to happen).

---

### Post by bingoUV on 2008-05-13
If you move, journalling is important for you. ext3 drivers in windows don't support journalling yet. So unfortunately you have to stick with NTFS.

---

