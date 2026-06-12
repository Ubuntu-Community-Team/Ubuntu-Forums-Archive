---
title: "Why can't I resize my partition?"
date: 2008-03-04
forum: General Help
---

### Post by brianbjjohnson on 2008-03-04
See the screenshot. I don't have the option to resize the partition I want to. I need to add more disk space to Windows (The top partition) but it is not letting me. Can I get some help please???

[[IMG]http://img215.imageshack.us/img215/5585/screenshotwu5.th.png[/IMG]](http://img215.imageshack.us/my.php?image=screenshotwu5.png)

---

### Post by ajgreeny on 2008-03-04
Maybe the windows partition is mounted.  Try right clicking in the partition in gparted and unmount it if it is, then try to do what you want again.

---

### Post by bodhi.zazen on 2008-03-04
You can not resize a mounted partition.

To resize your ubuntu root partition you need to boot a live CD.

---

### Post by -Zeus- on 2008-03-04
As bodhi.zazen said, you will need to boot some sort of cd in order to resize your ubuntu partition to add space to windows.  You can use the live cd for this task.

---

### Post by brianbjjohnson on 2008-03-04
> **-Zeus- said:**
> As bodhi.zazen said, you will need to boot some sort of cd in order to resize your ubuntu partition to add space to windows.  You can use the live cd for this task. And what do I do? I have the Live CD. I just don't wanna mess up bad.

---

### Post by slibuntu on 2008-03-04
If you;re running the live CD, going to Places->Computer, rightclicking the Windows volume and clicking un mount should unmout the windows volume and allow you to resize it.

Btw, 200th post!

---

### Post by bodhi.zazen on 2008-03-04
Back up and critical data (just in case)

Boot the Ubuntu CD

Start gparted

Resize

gparted Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by louieb on 2008-03-04
1st backup backup backup.
Boot to live CD
2nd you will have to shrink your Ubuntu partition (sd3) and move it to the right by the amount you want to add to your windows partition. Creating unallocated space between sda1 and sda3.
3rd. Grow partition sda1 (window) to fill the now unallocated space.

The shrinking and moving of sda3 is going to take some time could be 2-3 hours or more depending on the amount.

---

### Post by brianbjjohnson on 2008-03-04
So when I put in the Live CD. Which option do I choose?

---

### Post by brianbjjohnson on 2008-03-05
Ok I'm just about to do it. I just had a question when I'm resizing it. Does it matter what the value is where it says "Free Space Preceding (MiB)". Cause I have that set at 1. Does it need to be set to something specific?? I really need some help now!

---

### Post by brianbjjohnson on 2008-03-05
Bump... I really need to have this done by this afternoon. I have to record some classes on Windows for my school and I'm out of disk space on Windows, but have a TON on Ubuntu!

---

### Post by bodhi.zazen on 2008-03-05
It is hard to describe how to use a graphical program.

The link I gave you goes through resizing with pictures and is the best resource for your questions.

If you do not like the way it turns out, you can always resize, the changes are not permanent.

You are resizing your partition by reducing it by say 10 Gb == 10,000 Mb

Do you want the free, unallocated space to be in front or behind the partition ?

If in front -> 10,000 Mb in that box.

If behind, put 0 in that box.

Looking at your screen shot , I suggest in front.

Also you will need to do this in two steps, resize your ubuntu root -> apply changes -> resize windows - apply changes.

---

### Post by brianbjjohnson on 2008-03-05
> **bodhi.zazen said:**
> It is hard to describe how to use a graphical program.

The link I gave you goes through resizing with pictures and is the best resource for your questions.

If you do not like the way it turns out, you can always resize, the changes are not permanent.

You are resizing your partition by reducing it by say 10 Gb == 10,000 Mb

Do you want the free, unallocated space to be in front or behind the partition ?

If in front -> 10,000 Mb in that box.

If behind, put 0 in that box.

Looking at your screen shot , I suggest in front.

Also you will need to do this in two steps, resize your ubuntu root -> apply changes -> resize windows - apply changes. I get it now! Alright thanks! I'll be doing all that in an hour or so.

---

### Post by brianbjjohnson on 2008-03-05
OK. Now it is not letting me add to the Windows partition. I have a ton of unallocated space, but it won't let me add any of it to Windows! It won't let me make the Windows partition any bigger at all! It only allows me to make it smaller. The Windows drive is an NTFS. I don't know if that has something to do with it. A LITTLE HELP PLEASE?! :(

---

### Post by bodhi.zazen on 2008-03-05
Can you post another screen shot ?

---

### Post by brianbjjohnson on 2008-03-05
> **bodhi.zazen said:**
> Can you post another screen shot ? Yes. Just one minute.

Edit: [[IMG]http://img232.imageshack.us/img232/2294/screenshotmj0.th.png[/IMG]](http://img232.imageshack.us/my.php?image=screenshotmj0.png)

[[IMG]http://img126.imageshack.us/img126/1754/screenshot1yo5.th.png[/IMG]](http://img126.imageshack.us/my.php?image=screenshot1yo5.png)

The light blue partition is Windows.

---

### Post by gaussian on 2008-03-05
> **brianbjjohnson said:**
> OK. Now it is not letting me add to the Windows partition. I have a ton of unallocated space, but it won't let me add any of it to Windows! It won't let me make the Windows partition any bigger at all! It only allows me to make it smaller. The Windows drive is an NTFS. I don't know if that has something to do with it. A LITTLE HELP PLEASE?! :(

I am by no means an expert on partitions, but remember having read/experienced the following long time before (I have not have to deal with Windows partitions in a long time since all my computers run Ubuntu, Mandriva or OS X): depending on the choices made when the original NTFS partition was created your ability to grow or shrink the partition might be limited. This might or might not be the case here.

As a practical matter: why don't you use the empty space to create a second NTFS partition? Windows should see it as D: or something.

---

### Post by brianbjjohnson on 2008-03-05
> **gaussian said:**
> As a practical matter: why don't you use the empty space to create a second NTFS partition? Windows should see it as D: or something. Because the maximum of 4 primary partitions has been made. Thanks for the advice though.

---

### Post by gaussian on 2008-03-05
> **brianbjjohnson said:**
> Because the maximum of 4 primary partitions has been made. Thanks for the advice though.

Very good point, like I said I was not an expert on partitions. Now the question I have why do you have two separate Linux Swap partitions? Just delete one of them (the one you don't use) and you'll get your free primary partition.

---

### Post by ajgreeny on 2008-03-05
You need to move your sda3 partition as far to the right as possible first then you will be able to resize the sda1 partition to fill the space.  Do it in two separate actions if you prefer, but in theory you can set up both and then action both together.

---

### Post by bodhi.zazen on 2008-03-05
You need to move the unallocated space so it is adjacent to your ntfs partition.

You will need to move sda3, or resize sda3 and move the unallocated space to the other side ;)

---

### Post by gaussian on 2008-03-05
> **bodhi.zazen said:**
> You need to move the unallocated space so it is adjacent to your ntfs partition.

You will need to move sda3, or resize sda3 and move the unallocated space to the other side ;)

This is solid advice and I cannot believe that I missed this elephant in the room in my earlier post :)

---

