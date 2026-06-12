---
title: "Can't eject USB flash 2.0"
date: 2007-09-17
forum: General Help
---

### Post by Najmudin on 2007-09-17
I have a problem since i installed feisty on my computer , when i insert a USB 2.0 flash disk into my computer and adding some files to it after doing that i need to eject the USB but it can't be ejected 
some time it can be (rarely) , but at most times i cannot reject it form the computer and i got this 
message :

[IMG]http://img407.imageshack.us/img407/1129/usbproblemue6.jpg[/IMG] 

after getting this message i tried to press Eject again and it give another message 
"Cannot eject the volume"
How can i solve this problem cause it makes me suck and embarrassed me in front of my brother and friends:mad::mad::mad:

---

### Post by FuturePilot on 2007-09-17
Does the error message say anything about not being able to remove a directory? Expand the thing on the error message that says Details.

---

### Post by Najmudin on 2007-09-17
> **FuturePilot said:**
> Does the error message say anything about not being able to remove a directory? Expand the thing on the error message that says Details.

No , there is no more details it just said " Cannot eject volume "
i removed the flash disk but the icon is still there in my computer , when i double click on it 
it gives me this :
[IMG]http://img49.imageshack.us/img49/9081/screenshotgnomemountwu7.png[/IMG]

---

### Post by tmask on 2007-10-23
I have that exact same problem! It's driving me crazy!

Does anyone have the answer? I can't write any data to my flash drives.

---

### Post by buntunub on 2007-10-23
I have this problem too occasionally. My answer has been to open up the dreaded console and mount/umount manually. What I have noticed is that sometimes Gutsy seems to screw up the chown on the drives so that they get mounted as root instead of just a user. You can try it that way as both user and root (sudo) and see if that does the trick. If not, there may be a bug with HAL or dbus and you can try restarting those (sudo /etc/init.d/dbus restart). It looks to me though that your drive unmounted properly but just didnt register for some reason so it still "sees" it as being mounted even though its not.

---

### Post by vespo on 2007-10-23
Hi

the behavior you describe is perfectly normal, no bug at all.

First, you choose "eject" and the system writes down the cache to the disk. Depending on how big the files you copied were, how fast is the usb port/pendrive is, even how big the usb drive is, this process can take some time. 

When it's finished you just have to unplug the drive. At his stage, the drive is unmounted and that's why you cannot "eject" again, hence the error message.

After the first "eject", if you want to perform any action on the drive except unplug, you have to mount it again. (or unplug/plug it again)

Hope I explained clearly enough, otherwise i'll give more details later.

Cheers
vespo

---

### Post by kielpi on 2008-05-20
> **vespo said:**
> Hi

the behavior you describe is perfectly normal, no bug at all.

First, you choose "eject" and the system writes down the cache to the disk. Depending on how big the files you copied were, how fast is the usb port/pendrive is, even how big the usb drive is, this process can take some time. 

When it's finished you just have to unplug the drive. At his stage, the drive is unmounted and that's why you cannot "eject" again, hence the error message.

After the first "eject", if you want to perform any action on the drive except unplug, you have to mount it again. (or unplug/plug it again)

Hope I explained clearly enough, otherwise i'll give more details later.

Cheers
vespo

I think it shouldn't work this way. It simply should give no notification (or error message - according to you statement it is no error at all) and remove icon from desktop. Additionally power should be cut off of device on usb. So in my opinion this is a bug.All this actions should be taken of course after write down the cache.

---

