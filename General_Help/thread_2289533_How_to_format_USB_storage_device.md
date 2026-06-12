---
title: "How to format USB storage device"
date: 2015-08-04
forum: General Help
---

### Post by gordon33 on 2015-08-04
Hello All

When using Ubuntu 14.04 how do you format a new USB storage device?  

When the new USB storage is plugged in their is no USB icon in the bar.  If I go to "search computer" and type in "disk" and click on disk utilities the USB icon is there.  if I click on the USB icon the big box on the right changes with the message NO MEDIA in a orange box label VOLUMES.

I think I am close to the format USB just not making the correct selections.

Gordon33

---

### Post by ruzekle on 2015-08-04
Do you have gparted? If not, I suggest installing it. Here are some tutorials.

[https://www.youtube.com/watch?v=m9zctyRP434](https://www.youtube.com/watch?v=m9zctyRP434)
[http://www.howtogeek.com/howto/17001/how-to-format-a-usb-drive-in-ubuntu-using-gparted/](http://www.howtogeek.com/howto/17001/how-to-format-a-usb-drive-in-ubuntu-using-gparted/)

---

### Post by gordon33 on 2015-08-04
Hello ruzekle

Thank you for the quick reply.

I followed the "http://www.howtogeek.com/howto/17001...using-gparted/" after doing the install of GParted. 

Every thing went as shown until I was to pick fat32. Fat32 was not one of the options available.  So I picked ext4.  I was unable to fomat.  So, I went back to Gparteda and picked the last entry where the "unallocated" USB was.   That last line started with /dev/sda8 ...ext4  so i picked linux-swap.  Still could not format.  What did I do?  or what should i do now?

---

### Post by gordon33 on 2015-08-04
One message I got when trying fat32 was the partition required at least 33MiB.  This is a very small USB storage device.  only paid $2.00.

---

### Post by ruzekle on 2015-08-05
Do you get some sort of error when you try formatting?

---

### Post by gordon33 on 2015-08-05
Hello ruzekle

Only the messages above came up.  Odd is I installed the second USB storage device and it did not come up unallocated.  its as if the USB port is not recognizing the different new USB storage device.

Gordon

---

### Post by howefield on 2015-08-05
> **gordon33 said:**
> One message I got when trying fat32 was the partition required at least 33MiB.  This is a very small USB storage device.  only paid $2.00.

How large are the sticks ?

Good though gparted is, the Disks utility you mention above should also give you the option to format your disk.

---

### Post by gordon33 on 2015-08-05
Hello howefield

Thank you for your reply.

I can not find the size of the flash sticks on the packaging.

The flash sticks were purchased from one of the large office stores.  The packaging says: Ativa Micro Card Reader 405-988/24875299.  The back of the flash stick says: model USB 2 card, and model # PS 2008.

The packaging said it is compatible with several different windows versions and mac versions.  Linux was not listed.  But I thought any flash stick would work on Ubuntu.

Gordon33

---

### Post by howefield on 2015-08-05
Are you sure it is an actual USB stick and not an adapter into which you slot micro sd cards ?

---

### Post by Vladlenin5000 on 2015-08-05
> **howefield said:**
> Are you sure it is an actual USB stick and not an adapter into which you slot micro sd cards ?

You're right. It's just a dumb microSD card reader.

** It has no memory of its own ** -> You need to insert a microSD card in order to use it.

---

### Post by gordon33 on 2015-08-05
Hello Vladlenin5000, and howefield

Thank you for your help.

Embarrassed and yes it is a mini SD card reader.  I need to get out more.  

That solves this problem.

Gordon33

---

### Post by howefield on 2015-08-05
> **gordon33 said:**
> yes it is a mini SD card reader.

Ooops :)

> I need to get out more.

Back to the "one of the large office stores." then, that'll get you out for a little bit...

---

