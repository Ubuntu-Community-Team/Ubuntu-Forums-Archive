---
title: "Logitech Cordless Desktop s510 kernel patching help"
date: 2007-03-31
forum: General Help
---

### Post by nonamenoslogan0 on 2007-03-31
Well, it looks like i'm certainly not the only person on here with this problem...

I own a logitech cordless desktop s510, which comes with a media remote that isn't real functional. I found this post [http://www.qbik.ch/usb/devices/showdev.php?id=3816](http://www.qbik.ch/usb/devices/showdev.php?id=3816) which contains a kernel patch for it, and this post [http://www.ubuntuforums.org/showthread.php?t=229559&highlight=kernel+patch](http://www.ubuntuforums.org/showthread.php?t=229559&highlight=kernel+patch) which shows how to apply a kernel patch for a similar concer. I downloaded Linux Kernel in a Nutshell from here [http://www.kroah.com/lkn/](http://www.kroah.com/lkn/) so I think I can figure most of it out.

My question is, does that patch look alright? Do I just paste everything between the CODE tags into an empty file, and use that file in place of the file referenced in the MS Keyboard post? I don't know the first thing about building a kernel, so I'd just like to double-check before I potentially screw something up.

--UPDATE--

Well, I tried saving the patch in a file called "logs510-patchset" in the directory of the kernel source, linux-2.6.17.11 (the same kernel that i'm currently running, I don't care about the latest and greatest kernel). I then did the following, from that directory

```
steed@lain:~/linux/linux-2.6.17.11$ sudo patch -p1 < /home/steed/linux/linux-2.6.17.11/logs510-patchset
```

which gave me ```
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- drivers/usb/input/hid-core.c.default        2006-07-07 13:18:42.729408224 +0400
|+++ drivers/usb/input/hid-core.c        2006-07-07 03:48:15.389163680 +0400
--------------------------
File to patch:
```

i directed it to the file referenced in the patch, ```
 /home/steed/linux/linux-2.6.17.11/drivers/usb/input/hid-core.c
```

which gave me ```
File to patch: /home/steed/linux/linux-2.6.17.11/drivers/usb/input/hid-core.c
patching file /home/steed/linux/linux-2.6.17.11/drivers/usb/input/hid-core.c
Hunk #1 FAILED at 823.
1 out of 1 hunk FAILED -- saving rejects to file /home/steed/linux/linux-2.6.17.11/drivers/usb/input/hid-core.c.rej
can't find file to patch at input line 17
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|
|--- drivers/usb/input/hid-input.c.default       2006-07-07 13:18:58.151063776 +0400
|+++ drivers/usb/input/hid-input.c       2006-07-07 03:47:31.727801216 +0400
--------------------------

```

The patch i'm using doesn't look drastically different from the patch on the MS Keyboard post, so i'm having a hard time figuring out what i did wrong.

---

### Post by Sevmpe on 2007-04-27
Hi,

That's been taken care of in kernel 2.6.21 according to [bug 7352]("http://bugzilla.kernel.org/show_bug.cgi?id=7352"). There is a patch there that you might want to try. I wish I just had time to try it myself. If  you try it, please tell me if it works.

Cheers.]

---

### Post by KrazyPenguin on 2007-04-27
Very nice guide here to apply the patch:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

so it isnt' just copy and paste.

The new code must be complied.

See step #4

I just compiled the 2.6.21 kernel and it works, except to get my intel restricted wireless network card to work I need to compile this as well.

The first time always seems the hardest.....
:shock:

---

### Post by hebetude on 2007-11-10
Taken from [http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.22](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.22)

commit 529fa5473123a9e81e711a92e46fba732c4264ed
Author: Charles Pillar <pillarama@gmail.com>
Date:   Thu May 3 17:30:12 2007 +0200

    HID: add input mappings for non-working keys on Logitech S510 remote
    
    HID-input mapping for non-working S510 remote control buttons.
    
    Signed-off-by: Charles Pillar <pillarama@gmail.com>
    Signed-off-by: Jiri Kosina <jkosina@suse.cz>

---

### Post by yodauser on 2008-05-08
Hi there i just found a new software that might solve al the problem of USB driver issues with HID devices.. check out [http://www.hidpoint.com](http://www.hidpoint.com)

---

### Post by MatthiasM on 2008-05-08
Looks like a proprietary driver. Installing a third-party keyboard driver, that is closed-source and runs always in the background makes me feel to unsafe, sorry (keylogggers, etc.).

By the way: 
> You can now use all your extra function keys on a USB keyboard too. All required kernel patches are included since Linux kernel 2.6.24. Use this kernel (or a later version) in combination with keyTouch-editor 3.2.0 beta to create keyboard files for your USB keyboard. The created keyboard file can then be imported in the latest beta verion of keyTouch (version 2.4.0 beta). KeyTouch-editor 3.2.0 beta allows you to create one keyboard file for both a PS/2 and USB connection. So after you have added all the keys to the keyboard file while the keyboard was connected via USB, you can then connect the keyboard via PS/2 and set the PS/2 scancode of the key too. If discover any bugs in keyTouch-editor or keyTouch please report them. [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/) - maybe someone can package the latest keytouch beta version for Ubuntu 8.04 which uses kernel 2.6.24.

---

### Post by minimec on 2008-07-04
Hi folks.

Found your Thread about the s510 kernel patch...

I refer to the following post, because you gave me the idea for... THX

[http://ubuntuforums.org/showthread.php?p=5318355](http://ubuntuforums.org/showthread.php?p=5318355)


Our Logibaby works now...


minimec

---

