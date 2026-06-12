---
title: "mount points for unsafe removal flash drives"
date: 2014-04-02
forum: General Help
---

### Post by ulao2 on 2014-04-02
I have a situation for android and was hoping to get some advice from the Ubuntu community. Of course I tried the proper community but I dont think they really understand linux on the xda forums. That or my issues are always hard ones...

So in general what is going on is I have an app that mounts flash drives to mount points sda, sda1, etc... When I mount a flash drive to say sda and have to unplug it ( physically or dropping power to the hub ) the app using the mount point freezes up. When I reconnect the flash it fails to mount back to sda and then tries sda1. So now my app is lost because it does not know where the files are. 

So I'm trying to find a way to tell X device to always mount to sda. I think the solution is with the flash app ( stickmount ) but getting the author to comment is futile at best. I was hoping there was a may to marry the hardware ID to a mount point or something? I have root access but not sure what files to look at or if android has them.

Sorry for the crazy off-topic, just dont know where else to turn.

---

### Post by Double.J on 2014-04-02
Hi there!

woa! Tough one!

well i'll fess up, I don't know squat about android, but as it is linux, i'll provide the general linux info, see if it helps!

when you plug in a stick or drive or whatever into ubuntu, it is mounted at /media/nameofdevice on the OS filesystem - typically sda.

what you would want to do is use mkdir to create a folder to mount at... Say /mountstick.

then change the [label]("https://help.ubuntu.com/community/RenameUSBDrive") of the stick

finally edit the [/edit/fstab]("https://help.ubuntu.com/community/Fstab") file so that whenever a device with that label is inserted it will be mounted at your /mountstick folder.

you can skip the relabelling and just use the uuid of the drive. If you plan to ise a lot of cards this may be bad as there is a chance (remote) of two having the same uuid.

---

### Post by ajgreeny on 2014-04-02
Actually in the most recent verions of Ubuntu USB drives are automounted to **/media/<username>/name-of-drive**.

If you give the partition on a USB drive a label the **name-of-drive** mentioned above will be the label itself, much more sensible and useful than something like sda1 etc etc, as those device names can change if more than one USB is connected.

I would not bother to edit /etc/fstab for USB mounting in most situations as it is simply not needed if your USB partitions are labelled.

---

### Post by ulao2 on 2014-04-03
hmm thx guys!

also found this
Android has no /etc/fstab

You  don't need /etc/fstab to mount an partition. But there is IIRC no mount  command either.dev_mount should work (root required). All startup  system mounting is done with the/etc/vold.fstab helper script.

and also wondering if I can do this with mount --bind ?

---

