---
title: "Ubuntu Studio on usb with persistent cloud backup?"
date: 2017-03-24
forum: General Help
---

### Post by morgainebrigid on 2017-03-24
Hello all,
I have an idea of something I want that may not actually exist - yet. If it does, I don't know where to find it.
I tried to make a ubuntu-studio usb drive with persistent storage, so that I could use apps like GIMP and save the files on the thumb drive.
For reasons I don't care to go into, I have abandoned this idea.
What I would like to do now is create a non-persistent ubuntu-studio usb in which any files I create are backed up automatically to cloud storage without any deliberate action on my part.
Basically, I want to be able to plug a usb into one computer, use ubuntu studio to create a file, take out the usb, go to another computer and pick up where I left off.  Like making the usb persistent, but the persistent storage is in the cloud.
Does this make sense? Is it possible? Has it been done?

---

### Post by harrygray402 on 2017-03-28
You wouldn't be able to do this natively, AFAIK.  You would need some kind of partition mounted from a cloud storage provider. I'm pretty sure you could install Dropbox for linux and mount the Dropbox partition on your fstab. Whatever you write to that file system would get uploaded to Dropbox automatically.

---

### Post by Bucky Ball on 2017-03-28
You also have the issue of booting the stick on different machines. Some boot in UEFI, some in legacy. What is your USB going to boot into? I think there is a thing called 'multiboot' you can use for this and you may want to research, but can't help you there.

Also, it would largely depend on what exactly you are intending to do on UStudio with a USB. If you are intending to crank up Ardour and do some recording, not sure that will work. The USB will not be fast enough (although a USB3 dongle may work). 

For AV work (post-prod editing, large Gimp projects (maybe that's why you abandoned the other idea)), running the OS from a USB is definitely not advisable. The first sniff of HD video editing for example may see it fall over spectacularly.

(PS: harrygray402 is correct to a point, unless of course you have your own cloud and what your definition of the 'cloud' is. If you have your own webhost or server which you can reach remotely then that could work, too. Unsure of the finer details, they would be specific to setup, but again, if you were, say, recording live audio or video to the cloud, doubt it (although experimentation never hurt and happy to be proved wrong :)). Firstly the USB may be too slow, secondly the connection to the cloud will stall on the amount of data you are trying to upload ...)

---

