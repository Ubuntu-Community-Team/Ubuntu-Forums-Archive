---
title: "[SOLVED] Can't eject USB mass storage HD..."
date: 2007-09-01
forum: General Help
---

### Post by CD Baric on 2007-09-01
I have installed Ubuntu Feisty on a number of machines now and am very pleased overall -Well Done!

I have a few issues I hope to sort out soon:

(1) When I plug in my USB hard drive it appears on the desktop and a window opens howin me the contents. When I hit [eject] I am told I am unable to eject and the drive appears immediately.

I am able to eject USB flash drives without issue.

I am able to open a console and umount the USB hard drive but that is noob unfriendly - many of my installations are going onto new Linux users machines.

Is there a fix or work-around?

Thanks,

CD Baric

---

### Post by laidback on 2007-09-01
The only time I've had this is when an app or some other function is running from the drive. Check carefully that nothing has opened/run automatically when you attach the usb drive. Perhaps your music player?, maybe you have it looking for a music library on the hdd.

---

### Post by CD Baric on 2007-09-01
"maybe you have it looking for a music library on the hdd."

Nope - the window is closed and the drive in completely idle.

Did I mention that it unmounts in a console:

sudo umount /media/sdd1

It is just not very noob friendly and these system are going to noobs.

By the way, this same behavior is the same in all Ubunto installations I have tested.

eject [USB Flash] works no problem.

eject [USB HDD] does not work.

The USB HD is a 2.5" 80 gig HD in a small aluminum case - very handy. 

Thanks for the reply.

CD Baric

---

### Post by CD Baric on 2007-09-01
Is there some way to create an 'unmount volume' option on the mouse left-button menu when touching a mounted USB hard disk?

Come on guys, this is a real show-stopper!

CD Baric

---

### Post by laidback on 2007-09-02
Well I've used 2 usb hdd's, one 3.5" 250Gb fomatted NTFS + Linux and the other a 2.5" 20Gb NTFS formattted, both mount and unmount just fine. And on my system right click on a volume yields a Umount Option. I'm currently running 7.04, prevoiusly I had 6.10 and 6.06 both of which had the same options. I'm at a loss to know why your system doesn't have the same choices.

---

### Post by laidback on 2007-09-02
I wonder if it's the USB hdd connection that is giving you the trouble. I have tried a cable attachement (rather than hdd enclosure), with a 3.5" drive which didn't work properly in Linux, although it did work in XP (direct connection to the hdd with independent power supply, cheap but not cheerful). However, the 2.5 and 3.5 enclusures that I have do work. On my 250Gb 3.5" enclusure I have both NTFS and Ext3 partitions.

Another thought, Linux like the jumpers of the hdd set to master/slave rather than cable select.

---

### Post by PmDematagoda on 2007-09-02
I have no problem with ejecting USB drives myself, did this happen from the time you first used Ubuntu?

---

### Post by laidback on 2007-09-02
Reading your notes again I notice the line:-

sudo umount /media/sdd1

works. This implies that the drive/partition is owned by root, hence from your own desktop you won't be able to umount as you don't have permission. Why the difference between yours and mine is a mystery, must be something to do with the way you first attached the drive.

I'm out of my depth here but it's worth looking in:-

/etc/fstab

this file contains the partition descriptions used at boot up. Reckon you'll find your usb in there. Conclusion...it's attached at boot up under root ownership.
Solution....hum...you need other advice.

To view fstab fire up the terminal
david@Fawn:/$
then type after the $ sign
cat /etc/fstab

view the output on the sceen. (hint, make the terminal window wide as you need a bit of space to read the output lines)
You'll see things like

# /dev/hda1
UUID=1f9067aa-97a3-4de9-a4f2-84b6503ce58a /               ext3    defaults,errors=remount-ro 0       1

which is my hda1 drive definition. The line # /dev/hda1 is just for descriptive purposes.

---

### Post by dusu on 2007-09-02
Hi,

I do not know the answer to this problem, since I have exactly the same ! however this is with a usb stick.

In feisty, my usb stick is indeed in the group root
whereas in the older version of ubuntu I used (breezy :shock: ) it worked fine and was in the group "my_user_name"

well if someone has a clue, please tell !
this is indeed a pain to have something not working anymore when it worked perfectly fine before

thanks a lot !!

---

### Post by CD Baric on 2007-09-02
"And on my system right click on a volume yields a Umount Option."

Isn't that interesting.

On the three systems I have tried (all based on Feisty 7.04), all my USB mass storage devices show up with an 'Eject' switch, not 'Unmount'.

I have no problem unmounting my USB Flash devices, it is just the 2.5" HD mounted in the small aluminum cases that will not Eject.

Thank's for the information - now I now it is the HDs, not just Ubuntu.

CD Baric

---

### Post by CD Baric on 2007-09-02
"I have no problem with ejecting USB drives myself, did this happen from the time you first used Ubuntu?"

Yup, first time, every time on the three installations I have completed.

Thanks for the reply,

CD Baric

---

### Post by CD Baric on 2007-09-02
"This implies that the drive/partition is owned by root,"

Yup.

drwx------ 14 brian root    32768 1969-12-31 16:00 disk-3

This is what it looks like in /etc/mtab (fstab is only for permanently mounted drives)

/dev/sdd1 /media/disk-3 vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

As you can see, it is a vfat drive and has been mounted 'nosuid' - could that be the problem?

That gives me an idea.

Thanks for the feedback.

CD Baric

---

### Post by CD Baric on 2007-09-02
"In feisty, my usb stick is indeed in the group root
whereas in the older version of ubuntu I used (breezy  ) it worked fine and was in the group "my_user_name""

OK - Now I am very confused!

Here is what it looks like comparing an HD USB device and a Flash USB device in /etc/mtab:

/dev/sde1 /media/disk-4 vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
/dev/sdd1 /media/disk-3 vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

disk-3 is the HD USB device.
disk-4 is the Flash USB device

ls -l reveals:

drwx------ 14 brian root    32768 1969-12-31 16:00 disk-3
drwx------  5 brian root    16384 1969-12-31 16:00 disk-4

They look identical but attempting to 'Eject' the HD USB device gives me the following error:

[Cannot eject volume]

It actually looks like the drive is momentarily umounted but is immediately remounted along with the error message and the file manager window showing the contents.

Whereas using 'Eject' on the Flash USB device works perfectly - the drive disappears off the desktop and it is safe to remove from the USB socket.

I am going to file a bug report because this is a real dilemma.

Thanks for all the feedback, guys.

I will post any results as I find them.

CD Baric

---

### Post by dusu on 2007-09-03
> **CD Baric said:**
> "In feisty, my usb stick is indeed in the group root
whereas in the older version of ubuntu I used (breezy  ) it worked fine and was in the group "my_user_name""

OK - Now I am very confused!

Here is what it looks like comparing an HD USB device and a Flash USB device in /etc/mtab:

/dev/sde1 /media/disk-4 vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
/dev/sdd1 /media/disk-3 vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

disk-3 is the HD USB device.
disk-4 is the Flash USB device

ls -l reveals:

drwx------ 14 brian root    32768 1969-12-31 16:00 disk-3
drwx------  5 brian root    16384 1969-12-31 16:00 disk-4

They look identical but attempting to 'Eject' the HD USB device gives me the following error:

[Cannot eject volume]

It actually looks like the drive is momentarily umounted but is immediately remounted along with the error message and the file manager window showing the contents.

Whereas using 'Eject' on the Flash USB device works perfectly - the drive disappears off the desktop and it is safe to remove from the USB socket.

I am going to file a bug report because this is a real dilemma.

Thanks for all the feedback, guys.

I will post any results as I find them.

CD Baric

Hi,

I'll be glad if you find any way to fix this !
It is really strange that you have the same group 'root' for both disk3 and disk4 and that one can be unmounted and not the other one ! I thought that was the problem...
Now I understand nothing :)

Please post any news about this !

dusu

---

### Post by CD Baric on 2007-09-03
"Please post any news about this !"

Yes it is very confusing - I am going to have a look at how these things are auto mounted.

I will keep you apprised.

CD Baric

---

### Post by laidback on 2007-09-03
Still think it's worth looking in your fstab, does it refer to the problem usb drive?

---

### Post by CD Baric on 2007-09-03
> **laidback said:**
> Still think it's worth looking in your fstab, does it refer to the problem usb drive?

Removeable mass storage doesn't appear in the fstab (File System Table) - check for yourself.

CD Baric

---

### Post by aJayRoo on 2007-09-03
This is a known bug in 7.04. There are quite a lot of posts concerning it actually. Try this for a workaround:
```
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.backup
```
(and I think a reboot may be needed after). It will replace the eject option on the right click menu with unmount. I had the same issue but this works for me. Hope that helps.

---

### Post by Firippu on 2007-09-03
[http://ubuntuforums.org/showthread.php?p=2474560#post2474560]("http://ubuntuforums.org/showthread.php?p=2474560#post2474560")

---

### Post by aJayRoo on 2007-09-03
> **Firippu said:**
> [http://ubuntuforums.org/showthread.php?p=2474560#post2474560]("http://ubuntuforums.org/showthread.php?p=2474560#post2474560")

Yeah the advice from that link does pretty much the same thing as my previous advice but in a nicer way, as it saves having to remove any files where there might be other information that is needed (though this is not the case on my system). I would recommend the method from the link given by Firippu over the one I suggested previously.

---

### Post by CD Baric on 2007-09-06
Fantastic!

That fixed it!

I will repeat for all concerned:

------
Edit /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi and change the true at the end of:

<match key="info.category" string="storage">
<match key="storage.bus" string="usb">
<merge key="storage.requires_eject" type="bool">true</merge> 

to false, then restart hal.
------

That has fixed the problem perfectly.

Thanks for that,

CD Baric

---

