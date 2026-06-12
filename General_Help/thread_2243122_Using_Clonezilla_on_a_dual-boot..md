---
title: "Using Clonezilla on a dual-boot."
date: 2014-09-06
forum: General Help
---

### Post by Broghan on 2014-09-06
I have a question about Clonezilla. I just used Clonezilla to make an image of my entire drive. It only took a few minutes to complete but I noticed it threw up some error messages.  I'm dual-booting Ubuntu 14.04 with Windows 8.1. I'm wondering how I can test the image and if I should have just backed up the partions instead of the whole drive.  Thanks

---

### Post by yancek on 2014-09-06
I would expect cloning an entire drive to take longer than a few minutes depending, of course, on the size of the drives.  It would have helped if you made note of the errors to post.

---

### Post by Broghan on 2014-09-06
I know Windows is cloning correctly becasue it has no problem making the image or testing it but when I try to clone Ubuntu, I get an error that looks something like this, "Error failed to clone sda5." I'll have to run it again to look at the whole error, but that's pretty much it. I should mention that my home folder is encrypted.  Edit:  The errors are as follow, "Failed to use partclone program to save or restore an image!" "Failed to save partion /dev/sda5"  Update: I cloned the partitions separately and it worked. I just have one more question.  Listed as sda6, I have an unknown filesystem. I assume this is the swap but I'm a little confused as to why it's 8 GBs. Could someone clear this up?

---

