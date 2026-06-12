---
title: "[urgent] Completely remove ubuntu"
date: 2007-07-10
forum: General Help
---

### Post by Stex on 2007-07-10
My laptop is booked in for a repair job thanks to something going ary inside of it, thing is I haven't (and don't want to) mention linux. So I've got until 9 tomorrow morning to get rid of any trace of ubuntu.

Obviously it's a case of deleting the current partitions ubuntu is under and then resizing windows back to the full disc but I'm unsure what will happen to the boot. Will this get rid of grub and then leave the laptop unbootable? I do want to get rid of grub but obviously I need the windows loader to take over again.

The windows restore disc doesn't work which is a real pain and all the instructions I could find on the internet for uninstalling linux involved using it in some way. Does someone know the right way to go about this?

Also, in windows, my C drive is compressed. Could this pose a danger when resizing it's partition? I don't really mind about losing data but having a software problem mixed into the deal is only going to make this repair more painful for me.

Many thanks!

---

### Post by davecambs on 2007-07-10
why not mention linux, I can't see how this would affect an internal h/w error ?

---

### Post by moore.bryan on 2007-07-10
*what happens with the windows restore disk?  as far as i know, you just need to delete the partition(s) and restore the mbr.  [here]("http://www.geocities.com/mbrwizard/")'s a utility which may help if the windows restore disk problem is persistent.*

---

### Post by Stex on 2007-07-10
> **davecambs said:**
> why not mention linux, I can't see how this would affect an internal h/w error ?
Because it's a warranty repair. And in my experience they run off shouting obscenities if you even mention an alternative OS. It's a bit like filesharing to them: it's the source of every software, hardware and spiritual error known to mankind. I also asked on these forums and was agreed with that covering it up with windows was the easiest way to go.

> **moore.bryan said:**
> *what happens with the windows restore disk?  as far as i know, you just need to delete the partition(s) and restore the mbr.  [here]("http://www.geocities.com/mbrwizard/")'s a utility which may help if the windows restore disk problem is persistent.*
There's an error in the DVD, complains that it's packages are incomplete. Thanks for the link, I'll try that if there's no simpler way!

---

### Post by rillip on 2007-07-10
that  your drive is compresed would seriously complicate resizing it. I don't know what will happen.  It could ruin the partition, it could work fine. This is always the case, but when you add a complication, it makes the chance of failure go way up.

In regards to deleting the partitions, no, this will leave grub. If you go to the advanced boot screen (I think you have to hit something like F8 or F11 at a certain point in the boot process, it will tell you at the bottom), you might be able to boot into recovery mode (not safe mode) or a console session, something of the like.

From there you'll just need to run the command

```
fixboot
```

or

```
fixmbr
```

to restore your Windows MBR.  Not sure if this is doable with out the CD, but it might be possible to get to a recovery console from the boot menu, haven't tried.

---

### Post by blackeyeddog on 2007-07-10
If you boot from a CD , floppy disk or USB device containing basic Microsoft stuff (let's say , MS-DOS , Windows 95, 98 , etc.) , you can use the comand
A:> fdisk /mbr
to erase the Grub footprints. There are several easy ways to do this , tell me if you need more details.

This is basically the same nethod suggested by rillip with "fixmbr" and "fixboot" , only that these fix commands are for Windows 2000 and up.

If you really want to erase all traces of a non-Microsoft operating system , do also the following before erasing the partitions :

- boot some Linux live CD (Ubuntu's will be fine)

- umount the partition you want to wipe out completely , if it was auto-mounted . Let&#347; suppose it is /dev/hda2

- execute the command
# dd if=/dev/zero of=/dev/hda2 bs=1024 count=10000

This command will write all-zeros on the first 10000 blocks of the partition . A really good job will be to find the exact size of this  partition and use the count= parameter adequately.

---

### Post by bcmiller on 2007-07-10
You should fix your MBR as detailed above.

I wouldn't try to expand the windows drive.  Instead try to format the drive as Fat32 or NTFS and then put some documents and music on there.  It will appear like a reasonable safety precaution to keep your files safe from a corrupted windows install.

---

### Post by Stex on 2007-07-10
Phew! I kept getting a bad feeling about this one, but it's all gone well. Reshuffled everything through a live CD then cleared the mbr with an old 98 CD. Fantastic! They won't know what hit them, thanks everyone.

Now just to purge my internet history of all these linux forums :lolflag:

---

### Post by stchman on 2007-07-10
> **Stex said:**
> My laptop is booked in for a repair job thanks to something going ary inside of it, thing is I haven't (and don't want to) mention linux. So I've got until 9 tomorrow morning to get rid of any trace of ubuntu.

Obviously it's a case of deleting the current partitions ubuntu is under and then resizing windows back to the full disc but I'm unsure what will happen to the boot. Will this get rid of grub and then leave the laptop unbootable? I do want to get rid of grub but obviously I need the windows loader to take over again.

The windows restore disc doesn't work which is a real pain and all the instructions I could find on the internet for uninstalling linux involved using it in some way. Does someone know the right way to go about this?

Also, in windows, my C drive is compressed. Could this pose a danger when resizing it's partition? I don't really mind about losing data but having a software problem mixed into the deal is only going to make this repair more painful for me.

Many thanks!

Is this warranty work?  If so having another OS won't void the warranty.

---

### Post by marsbt on 2007-07-10
I would prefer to not send the HDD citing privacy concerns but if the hard disk is the problem I would have to think about it.

Plus, does you contact for the warranty say that you cannot run another OS on the machine? If it does, this is equivalent to a vendor lockin. I would rather go to a different shop the next time.

---

### Post by bcmiller on 2007-07-10
> **marsbt said:**
> I would prefer to not send the HDD citing privacy concerns but if the hard disk is the problem I would have to think about it.

Plus, does you contact for the warranty say that you cannot run another OS on the machine? If it does, this is equivalent to a vendor lockin. I would rather go to a different shop the next time.

When you don't have a lot of cash and you are dealing with a company that wants to get out of fixing your computer at no cost it's best not to rock the boat.

you could take a stand for your principles in the hope of making a better world but you'd just have a broken computer and the company would thank you for it.

---

