---
title: "So what is the status of the major scanner problem in Feisty 7.04 ?"
date: 2007-05-05
forum: General Help
---

### Post by episodic on 2007-05-05
I'm one of those that are severely affected by the scanner messup in Feisty. This really has got me about to have to go back to windows despite having every other thing working just fine in Feisty. Other than this issue I'm very happy. I have to have my scanner though. I've got one of the LIDE series that has been rendered impotent by the kernel bug. Makes no sense at all as I tried the 6.06 live cd before installing feisty - and it was supported with no problem. 

Thanks for informatio!

---

### Post by Schalken on 2007-05-05
If your scanner doesn't work, just install Windows in VMware and use your scanner through that. Thats what I do.

---

### Post by episodic on 2007-05-06
> **Schalken said:**
> If your scanner doesn't work, just install Windows in VMware and use your scanner through that. Thats what I do.

Why should I have to go through all of that trouble to simply scan an image when it worked fine in the last version? Don't mean to be short - but that is the point - I'm trying not to use windows anymore.

---

### Post by episodic on 2007-05-06
I really would appreciate an honest assessment of the situation. I am a relative newbie. I've read that recompiling the kernal might work - but at the same time - I've read that it did no good. Recompiling the kernal isn't something I really want to do. I've read that if you install scanbutton daemon and have it running it will allow you to scan without problems - I report that on Feisty that does nothing for a canon lide 20 scanner.

---

### Post by Stinger on 2007-05-06
It seems to be a kernel bug , somthing to do with the USB_SUSPEND option ,  but I dont understand how this kinda regression could pass into the final release of Feisty ???

You can read more about it here
[URL="http://82.211.81.186/showthread.php?t=389113"]
http://82.211.81.186/showthread.php?t=389113[/URL]

or here
[URL="http://82.211.81.186/showthread.php?t=414474"]
http://82.211.81.186/showthread.php?t=414474[/URL]

bugs are here

[COLOR="Red"][https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488]("https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488")[/COLOR]

here
[URL="https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/93515"]
https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/93515[/URL]

and here

[https://bugs.launchpad.net/ubuntu/+source/libusb/+bug/99802]("https://bugs.launchpad.net/ubuntu/+source/libusb/+bug/99802")

Kernelbug here
[URL="http://bugzilla.kernel.org/show_bug.cgi?id=8231"]
http://bugzilla.kernel.org/show_bug.cgi?id=8231[/URL]

Notice ! there seems to be a fix , now we can only wait until the developers decide to patch the current kernel.

[COLOR="Red"]As a temporarely workaround "scan button daemon" can be used
Read about it here[/COLOR]
[URL="https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/141"]
https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/141[/URL]

What a mess...

And if you take a look at this post it dosn't seem to be solved in Feisty at all......

[https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/180]("https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/180")

I simply dont know what to say...................

---

### Post by secular on 2007-05-06
This is a serious problem. I had to wipe my hard drive and install Edgy just so I could get some work done.

I hope the developers find a fix for normal users like me--users who don't know how to do Linux-style backflips.

---

### Post by joseelsegundo on 2007-05-07
yeah I'm having issues with the scanner in Feisty as well.  It seems that it will let me scan once and only once after booting.  If I try another scan I get the lovely I/O error.

But as a workaround, I booted from an edgy live CD and mounted my /home directory, used XSane off the live CD,  saved my scan images to my mounted home directory,  and then rebooted into my Feisty install as usual.  Kind of a pain, but I got the stuff I needed to be scanned done.

---

### Post by episodic on 2007-05-07
> **joseelsegundo said:**
> yeah I'm having issues with the scanner in Feisty as well.  It seems that it will let me scan once and only once after booting.  If I try another scan I get the lovely I/O error.

But as a workaround, I booted from an edgy live CD and mounted my /home directory, used XSane off the live CD,  saved my scan images to my mounted home directory,  and then rebooted into my Feisty install as usual.  Kind of a pain, but I got the stuff I needed to be scanned done.

How hard is it to mount your home directory under the live CD? I don't understand the 'edgy' monikor - what number version is that? Thanks.

---

### Post by joseelsegundo on 2007-05-07
Edgy is version 6.10.

Mounting your hard disk isn't too hard.  However you need to be careful not to mess with any system files.  If you are only messing around in your /home directory, you should be ok.

First you need to know the name of the filesystem on the hard disk you want to mount.  You'll probably want the root filesystem "/".  When you are booted into Feisty, do a "df -h".  This wil show the filesystems currently mounted. 

For me I have:

```
rob@boozoo:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  9.4G   25G  28% /
varrun                502M  100K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  108K  502M   1% /proc/bus/usb
udev                  502M  108K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   39M  464M   8% /lib/modules/2.6.20-15-generic/volatile
```

My root partition, "/", is at "/dev/hda1".  You will probably have something similar to this.  Maybe  /dev/sda1 for a SATA drive.

Once you have the file system name you want to mount it is pretty simple.

When you are booted into Edgy, do a

```
sudo mount /dev/hda1 /mnt
```

What this will do is mount the root partition in the /mnt directory.  So the path to my home directory is "/mnt/home/rob".

IMPORTANT:  when you are done mucking about close any applications that are using any files of directories on the hard disk.  Also close any terminal windows whose current dirctories are in the filesystem that you mounted.  Then unmount the filesystem:

```
sudo umount /dev/hda1
```

Hope that helps -
Rob

---

### Post by Ubimad on 2007-05-08
I am also suffering of that scanner problem. Needed regularly. Went even so far to try with Gentoo but you need a lot of time to do this baby, after a system update the wohle gentoo box was broken:lolflag: 
I really do not know what is so big about this USB Bug, it is really on the EXPERIMENTAL state, the Ubuntu boys should just release the same kernel without the USB Suspend, the the whole trouble is solved.
Regarding compiling a new kernel, is really a easy thing, if you have no ATI graphic or 3945 wireless like me, I would do it. Otherwise it is troublesome do make these hardware runing on a custom kernel. If anyone can help here:guitar: 
Install WMVARE Server and will run a Xubuntu 6.10 in it, there I can do all my scanner jobs.:confused:

---

### Post by episodic on 2007-05-11
Do the new updates that went out today have anything to do with the scanner problem? I noticed that it updated the HAL layer?

---

### Post by roberthr on 2007-05-14
It doesn't. Scannin with XSane or Gscan2PDF is still not possible.

What a shame. I really need scanning function to work properly :(

---

