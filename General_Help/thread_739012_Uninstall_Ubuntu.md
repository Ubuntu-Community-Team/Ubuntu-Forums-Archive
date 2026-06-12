---
title: "Uninstall Ubuntu"
date: 2008-03-29
forum: General Help
---

### Post by stiansoftcore on 2008-03-29
Ok, I know this might not be exactly the right place for even mentioning the name Vista, but I'll try.

I installed Ubuntu on my brothers laptop a few days a go, and it worked fine. But then he figured out it was "to hard for him to understand". He called i Unoobtoo. Well, he wanted Vista back, but now it won't install. I've tried fromatting every partitiotion on this laptop's harddrive into ntfs, but it won't work. When inserting the disc and following the steps, everything goes fine, until vista starts to "expand" it's files. It's not making progress, it stays at zero percent.

Some info:

What it says in Gparted on the Ubuntu disc:
Partition-----|..-Filesystem-|--Used-------|--Unused------------|--Size
-/dev/sda1--|-----ntfs------|---3.00 GiB---|--140.24 GiB  boot|--143.25 GiB
-/dev/sda2--|--extended--|----------------|-----------------------|--5.80 GiB
-/dev/sda5--|-----ntfs------|--51.41 MiB--|5.75 GiB------------|--5.80 GiB
-----------------------------------------------
The laptop is an Aspire 7520G:
*AMD Turion 64 x2 1,8 GHz
*It says "Up to 1024 MB Nvidia GeForce 8400 M G Turbocache
*2GB DDR2
*320 GB HD (160GB x 2)
-----------------------------------------------
What's weird is that it's a 320 GB HD, but Gparted doesen't even display the half of the space availabe.

Some info:

What it says in Gparted on the Ubuntu disc:
Partition      | Filesystem    | Used        |  Unused
-/dev/sda1  |  ntfs             | 3.00 GiB  | 140.24 GiB  boot
-/dev/sda2  |  extended    |     ---        |     ----
-/dev/sda5  |  ntfs             |51.41 MiB |  5.75 GiB
-----------------------------------------------
The laptop is an Aspire 7520G:
*AMD Turion 64 x2 1,8 GHz
*It says "Up to 1024 MB Nvidia GeForce 8400 M G Turbocache
*2GB DDR2
*320 GB HD (160GB x 2)
-----------------------------------------------
What's weird is that it's a 320 GB HD, but Gparted doesen't even display the half of the space availabe.

Does anyome know what to do?
----------------
**Updated:** Vista Install shows *Error Code: 0x80070017*

---

### Post by forrestcupp on 2008-03-29
It only shows half of the hard drive space because it is a 2 hard drive setup, hence the (160x2).  In GParted, it's only going to show one at a time.  In the upper right corner, you will see a drop down box that says something like **/dev/sda**.  If you click on that, it should have another option for **sdb** or something, which will show you the other half.

So in both of them, you need to delete **all** of the partitions and create new ntfs partitions that take up the entire amount.

---

### Post by ugm6hr on 2008-03-29
> **stiansoftcore said:**
> Ok, I know this might not be exactly the right place for even mentioning the name Vista, but I'll try.

True.

But if this had been posted as a "How do I uninstall Ubuntu?" thread, it would have been allowed (and perhaps attracted more pity help!)

Anyway - the hard drive size issue is not your problem with regard to installing Vista (160GB is enough), but we may as well get to the bottom of it.

Did Ubuntu install on sda or sdb?  I suspect that sdb (presumably the second hard drive) has been untouched by the Ubuntu installation.

You can check with:
```
sudo fdisk -l
```

As for why Vista won't install....

Did you wipe the Acer restore partition?  If not - try using that.

If you wiped that - is the Vista DVD an original, an Acer OEM, or one that you created from an Acer restore partition?  If the last, perhaps it didn't burn correctly.  If the second, try contacting Acer for a replacement (good luck - I couldn't find out how).  If the first - take it back for a replacement.

If a new disc doesn't solve the problem...  I dunno :(

---

### Post by stiansoftcore on 2008-03-29
Hmm, ok.. I haven't got that much experience with laptops, at least not Acer, so I just wiped both partitions, hoping it would have solved my problem. Really sorry for posting with wrong thread title.

---

### Post by Nythain on 2008-03-29
another thing i dont think has been mentioned...

remove the boot flag from any non windows partitions... Vista will refuse to install on a system with any "bootable" non windows partition... gotta love microsoft

---

### Post by Jimmy Johnson on 2008-03-29
While doing the Vista install you get the option to delete the current partitions, do it and let Vista make new partitions.

---

### Post by stiansoftcore on 2008-03-29
> **Nythain said:**
> another thing i dont think has been mentioned...

remove the boot flag from any non windows partitions... Vista will refuse to install on a system with any "bootable" non windows partition... gotta love microsoft
How do i remove flags? Gparted says only to change the flag. The only flag i have is on sdb, and the flag is boot.

EDIT: Never mind. But even after removing all the flags, Vista Install still won't "expand" it's files :/

---

### Post by stiansoftcore on 2008-03-29
> **Jimmy Johnson said:**
> While doing the Vista install you get the option to delete the current partitions, do it and let Vista make new partitions.

Not working :/ Gettiing really tired of Windows, Ubuntu was all plug and play, didn't even have to download drivers manually.

---

### Post by Nythain on 2008-03-29
how long did you wait... i noticed the vista installer/installation takes FOREVER, and at many points i had thought the install actually hung/locked up... patience and letting windows obliterate every existing partition and do its own thing is about all i got at this point

---

### Post by stiansoftcore on 2008-03-29
> **Nythain said:**
> how long did you wait... i noticed the vista installer/installation takes FOREVER, and at many points i had thought the install actually hung/locked up... patience and letting windows obliterate every existing partition and do its own thing is about all i got at this point
I waited until error code 0x80070017  showed up, so it's not my patience that is the problem :P I wish it was, though

---

### Post by sailor2001 on 2008-03-29
> **stiansoftcore said:**
> I waited until error code 0x80070017  showed up, so it's not my patience that is the problem :P I wish it was, though

[http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=728329&SiteID=17](http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=728329&SiteID=17)     the answer

---

### Post by stiansoftcore on 2008-03-29
nothing more? I'm kind of in a hurry =/

---

### Post by stiansoftcore on 2008-03-29
> **sailor2001 said:**
> [http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=728329&SiteID=17](http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=728329&SiteID=17)     the answer
I don't know how to enable the onboard video-driver on this laptop. 

But another thing, when I sat my BIOS options back to default, it said GRUB had an error loading, error 17? Why, I've formatted both of my disks :/

---

### Post by marine63 on 2008-03-29
smack him! who want's vista?

---

### Post by stiansoftcore on 2008-03-30
> **marine63 said:**
> smack him! who want's vista?

trust me, it is not I who want Vista, it's my brother ;)

---

