---
title: "gparted help"
date: 2008-07-02
forum: General Help
---

### Post by viperskunk on 2008-07-02
hi
i am using ubuntu 8.04 gnome desktop installed on one partition, and fedora 9 on the other. i would now like to resize the fedora partition and make it smaller, add the freed disc space to the ubuntu partition. however, i have a lot of data on the fedora partition that i do not want to lose. the website [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) says that it is possible to resize your hard disc without losing any data. is it really true? i do not know anything about gparted. could some please guide me through this (if it is possible on gparted)? i am really paranoid about losing data, as i do not have an external hard drive to store data on. nor do i have a fedora install cd. a friend of mine did it for me at school.
thanks

---

### Post by Victormd on 2008-07-02
Well, as long as you use gparted live CD or the gparted version included in the ubuntu live CD, you can resize your partitions without loosing your data. HOWEVER, it's never a good idea to do anything of this nature on your HD without backing up your data.
My suggestion would be to:
1. copy all the important data from your fedora partition to the ubuntu partition;
2. resize the fedora partition and make sure that all is Ok;
3. copy the data from the ubuntu partition back to the fedora partition (and check to see if everything is Ok) and only then, resize your ubuntu partition.

---

### Post by viperskunk on 2008-07-02
> **Victormd said:**
> Well, as long as you use gparted live CD or the gparted version included in the ubuntu live CD, you can resize your partitions without loosing your data. HOWEVER, it's never a good idea to do anything of this nature on your HD without backing up your data.
My suggestion would be to:
1. copy all the important data from your fedora partition to the ubuntu partition;
2. resize the fedora partition and make sure that all is Ok;
3. copy the data from the ubuntu partition back to the fedora partition (and check to see if everything is Ok) and only then, resize your ubuntu partition.
i am using gparted that came with the ubuntu installation cd. i do not have the gparted live cd. thanks. i will let you know how it went as soon as i am done with it.

---

### Post by dominiquec on 2008-07-02
Is the Ubuntu partition on a primary partition, and is the Fedora partition on an extended partition?  If this is the case, I think you'll run into some problem with expanding the Ubuntu partition.  You won't be able to do it without deleting the Fedora partition.

In the future, you might be better off separating your /home directory on its own partition.  This allows you to muck around with the operating systems without touching your data.

But of course it's always a good idea to back up.

---

### Post by Victormd on 2008-07-02
> **dominiquec said:**
> Is the Ubuntu partition on a primary partition, and is the Fedora partition on an extended partition?

Dominiquec has a good point. I'm assuming both your partitions are logical (this is the linux partition editor default - someone correct me if I'm wrong). Windows likes to create extended partitions and sometimes you'll run into problems with them.

---

### Post by bodhi.zazen on 2008-07-02
> **dominiquec said:**
> Is the Ubuntu partition on a primary partition, and is the Fedora partition on an extended partition?  If this is the case, I think you'll run into some problem with expanding the Ubuntu partition.  You won't be able to do it without deleting the Fedora partition.

In the future, you might be better off separating your /home directory on its own partition.  This allows you to muck around with the operating systems without touching your data.

But of course it's always a good idea to back up.

That is not true. If you are resizing a logical partition and adding space to a logical partition, first you resize the logical partition. Then the extended partition, then add the sapce to the primary partition. You may need to move the logical partitions so that the free space is adjacent to the primary partition, but you do not need to delete the logical partition ...

@viperskunk: You may have trouble if you installed Fedora into LVM. It can be done, but not directly with gparted. Either google LVM to see how to resize LVM partitions or see here 

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

Yes it is on LUKS (encryption) but *part* of LUKS is LVM ...

---

### Post by viperskunk on 2008-07-07
wow! thanks guys for the responses.i haven't got the slightest idea what a primary partition is, or whether fedora or ubuntu is on it. what i do know now, luckily for me, is that i managed to shrink my fedora partition without any trouble, and no data was lost. (gparted rocks!!!). i had made a back up of the most important stuff on DVDs; but there was still stuff i hadn't backed up. yet everything was there when i booted, and nothing was lost. now i am going to straightaway reinstall ubuntu, and use the newly created free space with the older ubuntu partition, and make them one.
thanks guys, once again!

---

