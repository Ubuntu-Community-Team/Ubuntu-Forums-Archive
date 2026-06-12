---
title: "Unable to copy files onto microSD card"
date: 2014-08-03
forum: General Help
---

### Post by mn_voyageur on 2014-08-03
I am having a similar problem ... except:

Last week, I copied my music and a few videos to an micro SD card for my tablet.  (Dell Venue running Android) 

Today, I removed the card to copy additional songs onto the card.  However, lack of permissions is preventing me from copying the files onto the card.

I have tried to change permissions:
     sudo chmod 666 -R  SDCARD/ (Also tried 777, 755)

Thanks,
MarkN

---

### Post by coffeecat on 2014-08-04
I have moved your post out of the thread you posted to as yours is almost certainly an entirely different problem. I've also moved it to General Help and given it a better title.

If the micro SD card is formatted FAT32, which it probably is, then you are wasting your time trying to chmod files on it. That is not how to change permissions on mounted devices formatted with a Microsoft filesystem. One possibility for your problem is that the filesystem on the SD card is damaged and that Ubuntu is mounting your card read only as a failsafe. Let's see if this is so. The output of the command below will tell us some useful things even if not.

Plug the microSD card into your Ubuntu machine, wait until it automounts, run this command and post the output:

```
mount
```

**EDIT**: A couple of other things.

If by chance you have installed the application usbmount, uninstall it. 

Your profile says Ubuntu 10.04 and your sig, Karmic Koala. Which Ubuntu release are you running? You might need to edit your profile and sig.

---

### Post by mn_voyageur on 2014-08-04
coffeecat

/dev/sdf1 on /media/SDCARD type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

Usbmount is not installed.

Thanks for the help.
MarkN

---

### Post by coffeecat on 2014-08-04
The card is being mounted read-write with the sort of permissions and options that are expected. It is formatted FAT so you won't be able to chown it. Nothing in that output tells us why you cannot write to it. In your first post you said:

>  However, lack of permissions is preventing me from copying the files onto the card.

What exact message did you see when you tried to copy files onto the card?

---

### Post by varunendra on 2014-08-04
Do you have a windows computer available? Is the card 'writable' there?

If yes, just "safely remove" the card from it (make sure you see the balloon pop-up that confirms you can safely remove it, before pulling it out), and retry in Ubuntu.

---

