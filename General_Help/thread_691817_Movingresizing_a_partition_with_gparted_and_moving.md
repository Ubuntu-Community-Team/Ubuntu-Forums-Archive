---
title: "Moving/resizing a partition with gparted and moving /home/"
date: 2008-02-09
forum: General Help
---

### Post by lszanto on 2008-02-09
Currently I have a 160gb harddrive divided into 3 sections, /home, / and unallocated space. I am trying to expand the /home partition to use all the unallocated space but it seems i cannot do this as it is not in direct contact with unallocated space and the / partition is in the way. If you don't understand the screenshot should explain it.

[Screenshot](http://img240.imageshack.us/img240/9231/screenshotuv3.png)

I'm not sure as how to move my partitons around so that I can use the unallocated space, any suggestions?

Thanks, Luke

---

### Post by cdtech on 2008-02-09
You'll have to use the gparted live cd to do any partition editing with your primary drive.

Once you boot into the gparted cd you'll have a much better understanding of sizing. You can select the partition and size it with your mouse.
I did a 250g hard drive with about 70g of information on it and took about 6 hours.

Good luck.

---

### Post by hyperair on 2008-02-09
From what I understand, your /home is not in direct contact with your unallocated space and so you cannot expand /home. The best way (that I can think of) to handle this is to shift both your /home and / partitions to the other side. Then expand /home.

For example, if your /home is at the beginning, followed by /, followed by <unallocated space>, you move your / partition to the end, then expand your /home since you have unallocated space to do so now. 

If I got this wrong, could you take a screenshot of gparted and post it here please?

---

### Post by lszanto on 2008-02-09
Yes thats correct, and the screenshot is in the above image link i just didn't post it as it was rather large. And to cdtech that doesn't work as i have to move my partitons/shift them to the otherside and i am unsure as to how to do this.

[http://img240.imageshack.us/img240/9231/screenshotuv3.png](http://img240.imageshack.us/img240/9231/screenshotuv3.png) - Screenshot

---

### Post by hyperair on 2008-02-09
Alright, here goes. Click /dev/sda2. Click Resize/Move. Make sure that number of bytes after the partition = 0, and the number of bytes that is in the partition is constant.

Click /dev/sda1. Click Resize/Move. Pull the sides until it uses all unallocated space.

EDIT: Oh you must use a livecd to do all that.

---

### Post by cdtech on 2008-02-09
> **lszanto said:**
> Yes thats correct, and the screenshot is in the above image link i just didn't post it as it was rather large. And to cdtech that doesn't work as i have to move my partitons/shift them to the otherside and i am unsure as to how to do this.

[http://img240.imageshack.us/img240/9231/screenshotuv3.png](http://img240.imageshack.us/img240/9231/screenshotuv3.png) - Screenshot

Agian, with the gparted cd. Once you boot into that cd you'll be able to size all partitions on that drive to any size you wish. You can delete, move, size whatever your heart desires. The image you display shows the partitions locked, you wont be able to edit them in that state.

---

### Post by lszanto on 2008-02-09
Okies i'll try that, yeah i have the gparted live cd which i used but i just got gparted up normally to show how the partition table looked, i know that i can't modify it when its locked :).

---

### Post by cdtech on 2008-02-09
> **lszanto said:**
> Okies i'll try that, yeah i have the gparted live cd which i used but i just got gparted up normally to show how the partition table looked, i know that i can't modify it when its locked :).

Its not hard really, just play around with it you don't have to comit to any changes until your ready to apply changes.  Try not to double up on steps. Once you have it the way you want try to do it with min steps. Move partition to the right, expand Move partition to left colapse for instance will be recorded and tend to slow the process down.

---

