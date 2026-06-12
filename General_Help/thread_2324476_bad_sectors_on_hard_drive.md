---
title: "bad sectors on hard drive"
date: 2016-05-14
forum: General Help
---

### Post by netopalis45 on 2016-05-14
I just purchased a new hard drive to replace a full and potentially failing drive I already had installed. After some googling I found that the easiest way to make sure that I got all my files transferred to the new drive was to use dd to clone the drive. When I did that it seemed to be working but would only copy a fraction of the drive over. I tried reformatting the drive and doing it again. Same result but with even less of the drive copied. I tried reformatting again but now I am getting an error that the drive has bad sectors and will not mount at all. I have run into a similar problem when trying to create bootable memory cards. Could there possibly be a problem with dd or at least the version I have of it?

I am using Ubuntu 14.04

---

### Post by peter228 on 2016-05-14
I would suggest two approaches - 

1.  Use a program called Disks to check the health of the hdd,   Go to Dash and enter Disks.  When the program opens select the hdd (i guess you will boot from Live media) and click on the horizontal bars in the top right of the program window.  There select SMART data and tests  and take a look at the result.  If the hdd has a problem you will be told here.

2.  To copy over your files I suggest you try grsync (has a gui) or rsync which is command line.  You will find in the repositories.  If anything is a problem the error reporting is very good and you will see clearly what went wrong and normally you can then figure out why ... 

I do not agree that dd is the best course of action here.  Sure it will clone the drive but it will also clone any problems.  If you are to simply copy off your data then grsync is your friend.

---

### Post by netopalis45 on 2016-05-14
I have been using Disks to try to set up the drive. It will no longer format or mount. It does show up in Disks but as a 4.1GB device (it is 2TB). When I select it and try to format it I get an error saying "Cannot mount /dev/sdi at /var/run/udisks2/block-format-tos-HHXp77: Invalid argument (udisks-error-quark, 0)"

---

### Post by peter228 on 2016-05-14
If you boot your system from Live media, I assume that you can see the new hdd listed there but probably not access the volume.

Can you launch gparted and then select the drive from the drop down list (top right corner of screen)?

If you can please delete everything that is there and then create a new file system..  If for some reason the drive is mounted you will need to unmount it first before you can do anything.  Select the drive and then right click and you will get the menu options .....

---

### Post by netopalis45 on 2016-05-15
It will not load in gparted. When I try to open it I get "Input/output error during read"

---

### Post by peter228 on 2016-05-15
hmmmm ....  that sort of sucks ..... 

It is tempting to suggest that this is a bad drive but ...  can we play it safe and check this?  A failing motherboard is able to create these symptoms as well .... 

Can you take this hdd to another computer and either install it internally or connect in a USB housing.  It the problem is the drive then the problem should follow to the new computer so if you were to run gparted then you would see the same thing happen....

---

### Post by Impavidus on 2016-05-15
That indeed sounds like a broken hard drive. I've got no experience with those. Somebody who has may drop in. In the meantime, have a read [here](https://help.ubuntu.com/community/DataRecovery). You may need ddrescue to clone to the new drive and then try and recover as much as you can. Don't write anything to that broken drive and don't read more than necessary, as it may damage the drive further.

---

### Post by netopalis45 on 2016-05-15
It turns out that the drive will not mount or be recognized by gparted on another computer. Fortunately, there is no data on the drive since it was to be a replacement for my current drive. I am going to try returning it and get another new one. Thanks for all your help

---

