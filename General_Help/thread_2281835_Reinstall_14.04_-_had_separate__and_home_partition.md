---
title: "Reinstall 14.04 - had separate \ and \home partitions"
date: 2015-06-10
forum: General Help
---

### Post by Quarkrad on 2015-06-10
After the re-install (making sure that only the \ partition was chosen to be re formatted) I have a new system but all the folders under \home are empty - as per a normal clean install.  My old \home appears, in nautilus, under Devices and I'm not sure what to do now - do I just just copy & paste.  This seems wrong to me in that my understanding is that the whole purpose of a separate \ and \home is that you can just re-install the os and maintain \home 'as it was'.  If I have to copy & paste I might as well have done a complete clean install and copy & paste from my backup.  Most surfing on this subject only goes as far as the 'do not choose the reformat \home partition' during the re-install - not much about post the process.   Is there a simple command that will put my old \home back to where it should be - and deleting the appearance of \home under Devices in nautilus?  I was hoping having separate \ and \home partitions  would speed up the reinstall process or add some added value - at the moment I'm in a slower/worst position than reformatting both partitions and copying & pasting.  I must have done something wrong.

---

### Post by QIII on 2015-06-10
Hello!

When you reinstalled, did you partition with "Something else" and make sure to un-toggle the "Do not use this partition" for your /home?  You should  make sure the format box is *unchecked ***and** the "Do not use..." is changed.

If not, then another /home, probably very small, was likely created.

---

### Post by Quarkrad on 2015-06-10
Thank you - yes, I did what you asked, I followed the procedure very carefully.  Gparted now shows my \ (sda5) partition as very small and \home (sda8) as it was before - (although it looks like some very small (1.27 and 1.4 MB) partitions have appeared - not bothered about those).  So I'm back to where I was before, partition wise.  Is this just a case of a pointing issue somewhere - i.e. do I have to tell something in \ that my\home is not in sda5 but in sda8?   I have to go out now for about 5 hours so will not be able to respond but would appreciated your help as I would like to get this sorted this afternoon.

---

### Post by QIII on 2015-06-10
I'm on the West Coast of the US, so it's late here.  Hopefully someone else will pick this up.

Can you post an image of your partition table in gparted?

Also, if you really want to give us some unnecessary overkill, you can give us the results of some of the following:

```
sudo fdisk -l
```

```
sudo df
```

```
mount
```

```
cat /proc/mount
```

---

### Post by Bucky Ball on 2015-06-10
Not sure if I understood you correctly, QIII, but if you want to use the existing /home partition (incidentally OP, it is a / forward slash, not a \ backward one, that is a Win thing) during 'Something Else' manual partitioning you mark it to 'Use' and NOT to format, not 'Do not use'. If you mark it as 'Do not use' the install will ignore the existing /home partition and create a /home directory inside the /. :)

I'm wondering if OP marked the /home partition as 'Do not use' and unticked 'Format' ... :-k The former is wrong, should be 'Use' and the latter is right, format should be unticked.

Incidentally, same applies for the existing /swap. Mark as 'Use'. Whether it formats or not is irrelevant as it is swapspace, but don't think you get the option to format or not anyhow ...

---

### Post by QIII on 2015-06-10
Maybe not clear...

Yes.  Change "Do not use" to "use" and make sure the format check box is unselected.

Could it be that it's time for sleepy little QIII to go to bed?  :)

---

### Post by Bucky Ball on 2015-06-10
> **QIII said:**
> Maybe not clear...

Yes.  Change "Do not use" to "use" and make sure the format check box is unselected.

Same page now. :) Trying to do a few things at once here! As usual ...

---

### Post by oldfred on 2015-06-10
About two thirds of the way down is screen shots showing the mounting of /home and not formatting it.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
He is using sdb6, so if you search for that it will located that part of example also.

---

### Post by Quarkrad on 2015-06-10
Thank you all - you have cracked it.  The problem is my lack of understanding of the install process using separate partitions.  When you say ** "Do not use" to "use"** there is not a **use** option in the drop down menu - do you mean use the jounaling system that exists - for me that is Ext4?  So .....  I highlight the /home partition, press Change and in the Use As: drop down window I choose Ext4 - and DO NOT tick the format box.

---

### Post by Bucky Ball on 2015-06-10
We're all learning as we go here. :)

Yep. Set as (use as) the mountpoint /home but DON'T tick to format. Same with existing /swap if there is one, but don't think you get the option to format or not as don't need to.

---

### Post by Quarkrad on 2015-06-10
Ubuntu back up and running - thank you all for your help and advice.

---

