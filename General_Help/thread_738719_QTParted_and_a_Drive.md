---
title: "QTParted and a Drive"
date: 2008-03-28
forum: General Help
---

### Post by Mr.Macdonald on 2008-03-28
I have been using Ubuntu for a long time ( in my 16 years of life ) and love it.

But i have had Windows dual booting in it. Please don't call me a sinner and banish me for blasphemy because I am now trying to format it to EXT3. I did as normal with QTParted but the disk keep formatting to and "unknown" in QTParted and a "VFat" in the System Monitor.

I don't understand.

My main goal is to have that EXT3 merge with my main one and form a seamless drive for my Ubuntu. They are 2 physical drives but my understanding is that a Linux will use both seamlessly.

Basically I want a EXT3 drive that won't mount in the "/media" folder.

I am comfortable with terminal and QTParted ( as far as I know ).

---

### Post by adult swim on 2008-03-28
im not sure from your post, but are you trying to remove windows and have one ext3 partition for ubuntu?

---

### Post by Mr.Macdonald on 2008-03-29
I have **2 Physical drives** one has Ubuntu install and the other **Had windows installed**

i recently formated that windows drive to an EXT3 with QTParted but in formated to unknown type in QTParted and to a vfat if i look at the file system type on Ubuntu.

I want it to be EXT3. (thats it)

on a side note i was wondering if Ubuntu will take that drive, once its EXT3, and merge it with my current drive so my **whole Ubuntu** is running off 2 physical drives

---

### Post by IceaTronic on 2008-03-29
Ok, firstly, it sounds like your trying to RAID the drives together, which cannot be done with out formatting BOTH of them. Say bye bye to data if you want that.

One solution (apart from your formatting issues, ill get to that in a sec) is to mount your 2nd harddrive as like a /data folder or what ever it is that you are going to put on there. For eg /home/music /home/pron /home/lotsofillegalstuff

Also, make sure you update fstab with this mount info as well, so you dont magically lose it after a reboot.

Now your formatting issues. personally i have never used QTParted before. try using fdisk or gparted or something like that to format your drive.

When using this fancy partitioning tool you have, what is it acctually saying or doing during the isntall? Are you making sure that you are selecting the ext3 FS type? what happens if you try formatting it to ext2?

Cheers,

IceaTronic

---

### Post by Mr.Macdonald on 2008-03-29
ext2 works great

thats really weird, i did the exact same thing for EXT3 and it failed!?!?!

I am happy with this but is EXT2 as good as EXT3.

i have heard that EXT3 is great because it defragments itself or something but what about EXT2

Is it as good or efficient?
Do i lose capabilities or something else?
Why might EXT2 have worked while EXT3 didn't, is the hard drive too old or something.

Also without unmounting it can I get the **icon** to stay off my desktop. I kind of bugs me. 
How do i change the permissions to all users, is it like normal> chmod -r 777 disk

Thank you

---

### Post by IceaTronic on 2008-03-29
Hmm, odd that it worked.

Ext3 is a journalled file system, and as such, in lamens terms, it defrags it self. Basically it just keeps better track of where everything is.

Ultimately, it boils down to what you want to put onto the drive.

My self, i have a 36gb SCSI and then 4x18gb SCSI in a RAID array.

My standlone drive is formatted to EXT3 while the array's are set to use ext2 due to the fact that they are for storage only. 

In all honesty, unless your running some bloody big apps that require lots of IO to the disk, you wont notice the difference.

Remember, to merge them as one, you will need to format, so read my advise above and just mount it to a folder some where. Tis simple :)

The icon on your desktop, well, i unno, i dont run a GUI, so thats a bit beyond me, id suggest just deleting/removing the icon, but then again, that may remove the drive mount as well.

If you want it accessible to all users, create a group, put them all in it and grant 777 access to that group if thats the path you wish to take. How many users will there be using said PC?

Cheers,

IceaTronic

---

### Post by Mr.Macdonald on 2008-03-29
I am the only user so 777 is no security loss

I still want to get that icon off my desktop or at least change the image of the icon. It just bugs me, i don't even know why

---

### Post by fjgaude on 2008-03-29
> **Mr.Macdonald said:**
> I am the only user so 777 is no security loss

I still want to get that icon off my desktop or at least change the image of the icon. It just bugs me, i don't even know why

I believe all you have to do is right-mouse click the icon, go to Properties at the bottom, and then click on the icon you see in the upper-left corner of the little window. Then click on Pixmaps, and there is where lots of icons are stored. Of course you can create your own icon and copy it there too.

---

### Post by Mr.Macdonald on 2008-03-29
Ok i have made some changes,

first i have partitioned that drive into three partitions and annoyingly  get **three icons on my desktop!!!**

this is bad because those partitions have special purposes,
[INDENT]
One is for my program development
One is for my web site (decent but not pro) [http://macdonald.webhop.org]("http://macdonald.webhop.org")
The last is for my ZIP/TAR installations ( don't ask )
[/INDENT]

the problem is that i already have appropriate symbolic links and i don't want the desktop icons

Mainly how do you get rid of the icons

---

