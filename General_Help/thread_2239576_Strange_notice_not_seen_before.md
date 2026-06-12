---
title: "Strange notice not seen before"
date: 2014-08-14
forum: General Help
---

### Post by RedRat on 2014-08-14
I recently got the notice of upgrades. When I attempted to do the upgrade I got this notice:

[ATTACH=CONFIG]255476[/ATTACH]
When I run sudo apt-get clean, nothing happens, the old files are still there.

Any suggestions as to what I am doing wrong?

---

### Post by grahammechanical on 2014-08-14
The images do not appear in your post.

---

### Post by coffeecat on 2014-08-14
> **RedRat said:**
> OK, I have a screen shot but for reasons only known to Firefox and the Ubuntu forum, it does not seem to show. basically it says to clear more free space in boot.

You dragged and dropped an image straight into the message editor and triggered a Firefox bug. Vbulletin doesn't work that way. You need to upload an image with the manage attachments button. *  I've removed the spurious base64 code. 

As far as your problem is concerned we probably don't need an image. It sounds as though you have filled your boot partition. Post the output of these two terminal commands:

```
df -h
ls -l /boot
```

One question: did you create a separate boot partition or did you choose an encrypted system when you installed Ubuntu?

* **Edit:** I see you've edited your post and done that now. You have indeed got an overfull boot partition.

---

### Post by RedRat on 2014-08-14
OK, here goes: 
df -h
```
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  453G  8.8G  421G   3% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         2.9G  4.0K  2.9G   1% /dev
tmpfs                        596M  1.4M  595M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.0G  1.4M  3.0G   1% /run/shm
none                         100M   72K  100M   1% /run/user
/dev/sda1                    236M  185M   40M  83% /boot
```

ls -l /boot
```
total 179531
-rw-r--r-- 1 root root  1158016 May  2 17:30 abi-3.13.0-24-generic
-rw-r--r-- 1 root root  1161713 May 15 12:07 abi-3.13.0-27-generic
-rw-r--r-- 1 root root  1161764 Jun  4 14:57 abi-3.13.0-29-generic
-rw-r--r-- 1 root root  1162257 Jul  4 15:18 abi-3.13.0-30-generic
-rw-r--r-- 1 root root  1162712 Jul 14 21:29 abi-3.13.0-32-generic
-rw-r--r-- 1 root root  1162712 Jul 29 10:41 abi-3.13.0-33-generic
-rw-r--r-- 1 root root   165510 May  2 17:30 config-3.13.0-24-generic
-rw-r--r-- 1 root root   165521 May 15 12:07 config-3.13.0-27-generic
-rw-r--r-- 1 root root   165544 Jun  4 14:57 config-3.13.0-29-generic
-rw-r--r-- 1 root root   165576 Jul  4 15:18 config-3.13.0-30-generic
-rw-r--r-- 1 root root   165611 Jul 14 21:29 config-3.13.0-32-generic
-rw-r--r-- 1 root root   165611 Jul 29 10:41 config-3.13.0-33-generic
drwxr-xr-x 5 root root     1024 Aug 12 17:12 grub
-rw-r--r-- 1 root root 19891718 May 15 21:09 initrd.img-3.13.0-24-generic
-rw-r--r-- 1 root root 19896611 May 26 18:39 initrd.img-3.13.0-27-generic
-rw-r--r-- 1 root root 19896419 Jun 15 10:23 initrd.img-3.13.0-29-generic
-rw-r--r-- 1 root root 19950046 Jul 14 17:54 initrd.img-3.13.0-30-generic
-rw-r--r-- 1 root root 19952556 Aug  9 11:00 initrd.img-3.13.0-32-generic
-rw-r--r-- 1 root root 19951741 Aug 12 17:12 initrd.img-3.13.0-33-generic
drwx------ 2 root root    12288 May  3 17:52 lost+found
-rw-r--r-- 1 root root   176500 Mar 12 05:31 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12 05:31 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12 05:31 memtest86+_multiboot.bin
-rw------- 1 root root  3372643 May  2 17:30 System.map-3.13.0-24-generic
-rw------- 1 root root  3377429 May 15 12:07 System.map-3.13.0-27-generic
-rw------- 1 root root  3378267 Jun  4 14:57 System.map-3.13.0-29-generic
-rw------- 1 root root  3378641 Jul  4 15:18 System.map-3.13.0-30-generic
-rw------- 1 root root  3381262 Jul 14 21:29 System.map-3.13.0-32-generic
-rw------- 1 root root  3381262 Jul 29 10:41 System.map-3.13.0-33-generic
-rw------- 1 root root  5776416 May  2 17:30 vmlinuz-3.13.0-24-generic
-rw------- 1 root root  5790912 May 15 12:07 vmlinuz-3.13.0-27-generic
-rw------- 1 root root  5792544 Jun  4 14:57 vmlinuz-3.13.0-29-generic
-rw------- 1 root root  5792608 Jul  4 15:18 vmlinuz-3.13.0-30-generic
-rw------- 1 root root  5798112 Jul 14 21:29 vmlinuz-3.1-32-generic
-rw------- 1 root root  5798688 Jul 29 10:41 vmlinuz-3.13.0-33-generic
```

No the installation was pretty vanilla, no encryption. Basically, just wiped the old 10.04 installation on my Serval Pro laptop.
Did nothing to sizing, if I recall just used the whole disk.

My question is why is sudo apt-get clean not doing its job?

---

### Post by coffeecat on 2014-08-14
> **RedRat said:**
> No the installation was pretty vanilla, no encryption.

Are you sure?

> **RedRat said:**
> ```
/dev/mapper/ubuntu--vg-root  453G  8.8G  421G   3% /

```

Is this familiar:

[img]http://ubuntuforums.org/attachment.php?attachmentid=255478&d=1408043343[/img]

The installer creates a separate 256MB boot partition when you choose an encrypted install because that has to be unencrypted. A lot of people are being caught by this by not clearing out old kernels occasionally. In my opinion, 256MB is not large enough and the person installing has no way of changing this, but that's another story.

But anyway, the important thing is that you need to uninstall all the kernels except the newest one or two. **Don't** delete the files manually in /boot. You need to use the package manager to do this properly. Do you need help with this?  

By the way, I changed the quote tags in your last post to code tags to preserve formatting. You need code tags for terminal output or config files.

[ATTACH=CONFIG]255478[/ATTACH]

---

### Post by ajgreeny on 2014-08-14
I'm afraid **sudo apt-get clean** will not help you in any way.  All that does is remove all package files from the cache that is sitting in /var/cache/apt/archives, and that is exactly what the name suggests; a cache, nothing to do with booting or running your system.

If you installed with no encryption and without choosing to use a separate /boot partition you would have ended with just three partitions, root or /, an extended partition, and within that extended partition a swap partition of the exact same size.

You must have chosen to use a separate /boot partition at some point or it would not exist; or did you perhaps choose Something Else at partitioning stage and then reuse all the partitions that you saw in the old 10.04 installation?

---

### Post by Impavidus on 2014-08-14
```
sudo apt-get --purge autoremove
```may help to uninstall old kernels. If that doesn't work (because the update is already partially installed), you'll have to use dpkg directly. Run```
dpkg --list linux-image*
``` to get a list of installed kernels. Make the terminal wide enough, else the output won't fit. It will show the exact names of the packages, of which you'll have to uninstall the oldest versions with```
sudo dpkg --purge linux-image-<possibly something>3.2.0-<something>
```

---

### Post by RedRat on 2014-08-15
> **coffeecat said:**
> Are you sure?



Is this familiar:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=255478&d=1408043343[/IMG]

The installer creates a separate 256MB boot partition when you choose an encrypted install because that has to be unencrypted. A lot of people are being caught by this by not clearing out old kernels occasionally. In my opinion, 256MB is not large enough and the person installing has no way of changing this, but that's another story.

But anyway, the important thing is that you need to uninstall all the kernels except the newest one or two. **Don't** delete the files manually in /boot. You need to use the package manager to do this properly. Do you need help with this?  

By the way, I changed the quote tags in your last post to code tags to preserve formatting. You need code tags for terminal output or config files.

[ATTACH=CONFIG]255478[/ATTACH]

No that does not look familiar. basically I told it to use the whole disk for my 14.04 installation. I did not see anything about encryption when I did this. Further, I was never asked for a security key. 

Thanks for any clearing up of tags.

---

### Post by RedRat on 2014-08-15
The purge command did not work.

However when I list the images: 
```
||/ Name              Version       Architecture  Description
+++-=================-=============-=============-========================================
un  linux-image       <none>        <none>        (no description available)
un  linux-image-3.0   <none>        <none>        (no description available)
ii  linux-image-3.13. 3.13.0-24.47  amd64         Linux kernel image for version 3.13.0 on
ii  linux-image-3.13. 3.13.0-27.50  amd64         Linux kernel image for version 3.13.0 on
ii  linux-image-3.13. 3.13.0-29.53  amd64         Linux kernel image for version 3.13.0 on
ii  linux-image-3.13. 3.13.0-30.55  amd64         Linux kernel image for version 3.13.0 on
ii  linux-image-3.13. 3.13.0-32.57  amd64         Linux kernel image for version 3.13.0 on
ii  linux-image-3.13. 3.13.0-33.58  amd64         Linux kernel image for version 3.13.0 on
ii  linux-image-extra 3.13.0-24.47  amd64         Linux kernel extra modules for version 3
ii  linux-image-extra 3.13.0-27.50  amd64         Linux kernel extra modules for version 3
ii  linux-image-extra 3.13.0-29.53  amd64         Linux kernel extra modules for version 3
ii  linux-image-extra 3.13.0-30.55  amd64         Linux kernel extra modules for version 3
ii  linux-image-extra 3.13.0-32.57  amd64         Linux kernel extra modules for version 3
ii  linux-image-extra 3.13.0-33.58  amd64         Linux kernel extra modules for version 3
ii  linux-image-gener 3.13.0.33.39  amd64         Generic Linux kernel image


```

If I run
```
sudo dpkg --purge linux-image-<possibly something>3.2.0-<something>
```

That would wipe out my existing kernel since that is in /boot. Naturally I am a bit leery of running that code.

Perhaps, at the end of the day, I should just re-install 14.04LTS from the disk and wipe the disk completely, since I don't have a lot invested in this particular installtion which is only a few months old.

---

### Post by ajgreeny on 2014-08-15
The easiest way to sort this out now is to install synaptic (package manager), open it, reload the packages list with far left icon in toolbar, then search for **linux-image** by "Name" only, not "Description and Name".

That will list all kernels, show those installed, and allow you to "Mark for Complete Removal" the old ones you don't need any more.  This will also show you just how brilliant synaptic is when compared with the software-centre; it is what I almost always use for installing, uninstalling or updating packages on my system as it is so much more flexible, giving you a lot more detail about what is happening than anything except the command line, and in fact you can set synaptic to "Apply Changes in Terminal Window" which shows all that would show from an apt-get command.

There is no real point in re-installing the OS if it otherwise working as you want, so go to synaptic and see what you've been missing.

---

### Post by RedRat on 2014-08-15
That worked!!! I selected the image with the lowest number, linux-image-3.13.0-24.47, had complete removal. That freed up the necessary space.

The synaptic trick is a good one, but I have been burned by it too! You might see my other post in which I used synaptic and my Grub2 wiped out and replace with some very old version, 1.99 and it kind of screwed my system. However, I suspect that perhaps some of the screwed up state might also be contributed by a failing computer. I am now in the market for a new machine that is preloaded with Windows (7 or 8) on which I can also install Ubuntu along side it. That, unfortunately, seems also fraught with difficulties due to bugs in the Ubuntu installer. I don't need this drama:wink:

I think I will use synaptic to clear out some of those older versions. It is too bad that the magicians at Canonical can't devise such a tool. 

Thanks again.

---

### Post by Impavidus on 2014-08-15
Yes, synaptic is great, but if the package system is already in an inconsistent state apt-get or the software centre might refuse to install it right now. That is suggested by the not working apt-get autoremove command, although not confirmed by dpkg --list. So if you can install synaptic, that would be good. Else, read on.

The dpkg command will uninstall all old kernels whose version numbers you fill in for <something>. So I think you can use dpkg to uninstall```
linux-image-3.13.0-24
linux-image-3.13.0-27
linux-image-extra-3.13.0-24
linux-image-extra-3.13.0-27
et cetera
```Just keep your current kernel and the one before for now, which are version 3.13.0-32 and 3.13.0-33 (I assume). That should free enough space.
(OK, kernel 3.13. In my previous post I mistakenly wrote 3.2, which is for 12.04)

As in```
sudo dpkg --purge linux-image-3.13.0-24
```

---

### Post by RedRat on 2014-08-15
When I run that command I get the following warning:
```
dpkg: warning: ignoring request to remove linux-image-3.13.0-27 which isn't installed

```

Any ideas?

The synaptic approach did work.

---

### Post by ajgreeny on 2014-08-15
> **RedRat said:**
> When I run that command I get the following warning:
```
dpkg: warning: ignoring request to remove linux-image-3.13.0-27 which isn't installed

```

Any ideas?

The synaptic approach did work.
You can ignore that error; it's not actually an error but is telling you that version was removed already in some way.

Having now got synaptic, it is worth checking every so often to see how many kernels you've got and removing all but the two most recent.  I do that after every kernel upgrade that appears in upgrades.

---

### Post by coffeecat on 2014-08-16
@RedRat, hopefully you have managed to make some room in your /boot partition, but it would be helpful if you could confirm something. Another forum admin and I have been discussing the fact that threads for help because of too-small boot partitions are becoming common and we were looking into whether there was anything we could do about this. I was distracted by encryption, so I wasn't clear before, so I apologise for that and I also needed to check something out. Please have a look at this new screenshot and compare it to the one in my post #5 which you have already responded to.

[img]http://ubuntuforums.org/attachment.php?attachmentid=255519&d=1408187692[/img]

Did you perhaps choose LVM without encryption? (You may have seen more choices before the encrypt and LVM choices - I was presenting the installer in both cases with a blank drive.) The reason I ask is that this:

> **RedRat said:**
>  
df -h
```
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  453G  8.8G  421G   3% /
<snip>
```

Specifically "/dev/mapper/ubuntu--vg-root", is what you get when you choose LVM with or without encryption. And the problem is that the installer creates a separate /boot partition of slightly under 256MB, which quickly gets filled up, if you choose LVM with or without encryption.

A bug has been raised:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

Unfortunately, Elfy and I were both focussed on encryption when we were discussing this, and LVM whole disc installation is really the issue, not encryption. We'll see about amending that bug report, but in the meantime it would be useful to know anything you can remember about when you installed your system.

---

### Post by RedRat on 2014-08-16
coffeecat
I know that I did not choose encryption--I am not that crazy. The last thing I need is to try to remember some encryption key. As to the LVM, I must say that I just don't remember! I set that up several months ago and because I was upgrading my System76 ServalPro, I had several other issues with the upgrade that the folks at System76 helped with. I cannot remember if that choice was there in my setup window as you point out, it might have been there by default. I do know that if it was, I would have unchecked the damn encryption choice for sure. Why the developers would make encryption a default choice is beyond me. That is something only someone who really needed and wanted encryption security would choose freely and knowingly. I might have left the LVM checked, but honestly I cannot remember. 

Since you raise the issue, is there a way to increase the /boot size? Simply! I can clear out the older images using synaptic (and have done so) but that can become annoying after a bit. I have already freed up space. 

Hope this helps.

---

### Post by coffeecat on 2014-08-16
Thanks for that feedback. The bug report has been amended to include both encrypted and non-encrypted LVM installs. 

Just a FYI. The installer definitely doesn't tick the encryption box nor the LVM box by default - at least when I tried some test setups. That indeed would be poor design.

As far as increasing the /boot size, I honestly don't know. If you had an installation to conventional partitions this would be fiddly but doable. But all the hard drive space apart from the boot partition is a LVM volume which complicates things. I have avoided LVM like the proverbial barge-pole - except when doing test installs. A bit like you with encrypted installs! :wink: So I don't have the hands-on experience to advise. Perhaps someone else can. But so long as you remember to keep only the 2 most recent kernels, you should be OK. If you see a new kernel in the upgrades, then uninstall the oldest once you have tested the newest to be sure that it hasn't introduced its own problems, leaving two. It's a good idea to retain the immediate previous one, just in case.

---

