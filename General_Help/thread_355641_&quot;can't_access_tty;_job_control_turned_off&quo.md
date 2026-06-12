---
title: "&quot;can't access tty; job control turned off&quot;"
date: 2007-02-07
forum: General Help
---

### Post by Naetholix on 2007-02-07
Ok, I'm a new Ubuntu user, and I just installed my Edgy Eft OS a few days ago.

I've already fished through some problems with the Xserver and Xorg, so I'm a little familiar with the Terminal.

Here's my problem:

I have two HD's, and only one of them was showing up in my Desktop.  I searched the online forums and such, and found a walkthrough using a disk mounting method with the fstab.  I changed a few fstab values according to the walkthrough and saved it.  I thought I was doing the right thing, and when I rebooted my OS, I got this:

*/bin/sh: can't access tty; job control turned off*

And it goes to the blinking cursor.

I'm real sorry if this is another monotonous post of the same topic, but all the searches I found came up with a similar problem but no solution, or the problem was solved in all this programmer language that I don't understand too well.

I would appreciate it a lot if someone could help me out and guide me through to getting my desktop back without having to reinstall Ubuntu.

---

### Post by kebes on 2007-02-07
Perhaps you made a small mistake in your "/etc/fstab" that broke it. Did you save your previous fstab before changing it?

Try booting into your Ubuntu install/LiveCD, and then mount your hard-drive. You can do this on the commandline with something like:
mount /dev/hda1 /mnt/drive

(Of course it will depend on what your drive is actually called, "hda1" is just an example, and you need to make a directory, such as "/mnt/drive" to mount at.)

Then go into your hard-drive and change your fstab back to the way it was before. You can post the fstab here and maybe someone will spot a mistake in it.

---

### Post by Naetholix on 2007-02-07
It is highly probable that my fstab was done wrong; I was experimenting with it to work with the HD mounting and added some values.

I attempted running the LiveCD and making the changes, but I don't get the same fstab layout.  It's a lot more bare (only two lines) than when I edited the fstab running off my HD.  If I could get to that fstab, I definitely would post the information here.

Another thing that might be important.  When Busy Box starts (after failing to boot my OS), it gives me that message ("/bin/sh: can't access tty...") and the cursor follows this phrase:

(initramfs) *blinking cursor*

And every course of action I take, the resultant command line follows that /bin/sh: directory.

*type "sudo nano /etc/fstab"*

And I get:

/bin/sh: sudo: command not found
(initramfs) *blinking cursor*

---

### Post by kebes on 2007-02-07
Yeah that "(initramfs)" is a very basic shell that isn't useful for much. It just means that the boot failed before getting very far along. (Note: sometimes if you just press enter at that prompt booting continues normally... but typically that prompt is just useless.)


When you boot into the LiveCD session, you are running off of the CD, not the hard-drive. So if you just go and check "/etc/fstab" you will be looking at the fstab for the LiveCD session.

This is why in my last post I said you have to mount your hard-drive, and navigate into it to see the fstab file saved on the hard-drive.

To do so, you should go to a terminal (Applications > Accessories > Terminal), and follow these steps:

1. Determine what your hard driver partition with Linux is "called." To do this, type:
```

sudo fdisk -l

```

This will list the partitions detected. Based on the order, sizes, and types, you should be able to know which one is the Linux partition.


2. Mount this partition. First make a directory:
```

cd /media/
mkdir mydrive

```

Then mount it:
```

mount /dev/hda1 mydrive

```

Change the "hda1" to whatever your actual partition is.


3. Once mounted, go into this mounted-drive and go find your fstab:
```

cd mydrive/etc/
more fstab

```


If everything worked, then that last command will have printed out the contents of the fstab on your hard drive. You can use the commandline text editor "nano" to modify it, change it back, etc.

If you run into problems post the contents of your fstab here, or post any errors you get. Some of the above commands might require that you put "sudo" in front of them for them to work. (Because you need root power to perform the action.)

---

### Post by Naetholix on 2007-02-07
I did everything as instructed.  I managed to change the values back the way they were in my fstab.

But I still get the same error at startup.

/bin/sh: can't access tty; job control turned off

Any ideas?  If worst comes to worst; I'll have to reinstall Ubuntu, but I don't want to have to do that.

---

### Post by kebes on 2007-02-07
Hmm... that's strange. The error you are seeing normally happens when the motherboard is not properly recognized by Ubuntu... but you said you had everything working for awhile.

I'm not sure what's going on, but here's something to try: When it gets to that annoying error message, press Ctrl+Alt+F1 (cycle through Ctrl+Alt+F1 all the way to Ctrl+Alt+F12 if you have to...). You should see a list of kernel messages. There will probably be a bunch of error messages somewhere.

Hopefully those errors will provide a clue as to what aspect of the boot is failing.



P.S.: If Ctrl+Alt+Fn doesn't work, try just Alt+Fn

---

### Post by Naetholix on 2007-02-08
Ok, I hit that key sequence in the shell, and I got this:

"Calling INT 0x1A (F000:FE6E)
EAX is 0xB102

Calling INT 0x1A (F000:FE6E)
EAX is 0xB102

mount: Mounting /dev/hda1 on /root failed: No such device

mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory

mount: Mounting /sys on /root/sys failed: No such file or directory

mount: Mounting /proc on /root/proc failed: No such file or directory

Calling INT 0x1A (F000:FE6E)
EAX is 0xB102

Calling INT 0x1A (F000:FE6E)
EAX is 0xB102

Target file system doesn't have sbin/init"

That's it.  Is there anything I can do with that?

---

### Post by Inhumane on 2007-02-08
I'm getting the same problem, only it happens after I try to recompile my kernel to 2.6.20, you can see my thread here: [http://ubuntuforums.org/showthread.php?t=353661](http://ubuntuforums.org/showthread.php?t=353661)

I really don't understand what's going on. I can boot fine to the old kernel that came with Ubuntu, but not the new one

My FSTAB looks like this:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=698b957e-528b-4ee3-a3d8-e9b531b9f352 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=484e0c25-584b-4458-83a1-c3eb4efde244 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

I'm having a hard time decrypting it

---

### Post by kebes on 2007-02-08
Hmm... I'm not sure.

This is what I would do:

1. Boot into LiveCD, check the contents of "/etc/fstab" and of "/boot/grub/menu.lst" and see if something looks wrong. (You can post these files to this thread if you want.) Sometimes fstab will have the device names (like /dev/hda1) replaced with weird designators (like UUID=001929828) and this can cause problems.

Compare your menu.lst to examples you find online. Make sure that the partition you are trying to boot is the right one. (In your menu.lst it will list "root (hd0,0)" or whatever... make sure that this is the right one... refer to grub docs if needed.)


2. While you're at it, perhaps run a disk check on your hard drive (commandline "fsck"). Maybe there's something wrong there.


3. At boot time, there are usually multiple options for booting Ubuntu. Something like:
ubuntu 2.6.17
ubuntu 2.6.15
ubuntu 2.6.17 (recover mode)
ubuntu, memtest

Do any of those work? Can you get in with an older kernel? In recover mode?


4. It's ~possible~ that the grub bootloader is somehow corrupted. You could try reinstalling it. To do so, from a LiveCD session you would use the commands "grub" and/or "grub-install".


Those are all the ideas I have for the moment... good luck.

---

### Post by kebes on 2007-02-08
> **Inhumane said:**
> I'm getting the same problem, only it happens after I try to recompile my kernel to 2.6.20, you can see my thread here: [http://ubuntuforums.org/showthread.php?t=353661](http://ubuntuforums.org/showthread.php?t=353661)

I really don't understand what's going on. I can boot fine to the old kernel that came with Ubuntu, but not the new one

My FSTAB looks like this:

I'm having a hard time decrypting it

Read the post I just put for Naetholix. Basically try to boot with older kernels at the grub prompt. If those work, then just stick with them!

Also, your fstab has that strange UUID thing that I've seen before. I would try reverting that (I have no idea why it sometimes happens). So basically backup your "/etc/fstab" which looks like this:
```

 # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=698b957e-528b-4ee3-a3d8-e9b531b9f352 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=484e0c25-584b-4458-83a1-c3eb4efde244 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

```

And change it to look like this:
```

 # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

```

All I did was remove the comment (#) from those two lines, and deleted the UUID thing. The UUID is supposed to be equivalent to the /dev/sda# designation, but from what I've seen this is sometimes the problem.

Anyways, it's worth a try. If it doesn't work, you can revert your fstab.

---

### Post by Inhumane on 2007-02-08
I tried changing my fstab to the one you posted above, no luck.

I would also like to try out the CTRL+ALT+F1 trick but my mouse and keyboard are non functional under that kernel it seems

---

### Post by doggie on 2007-02-09
I had the same problem... what I did was:
look for /etc/fstab, /boot/grub/menu.lst

my menu.lst is something like:

```
title		Ubuntu, kernel 2.6.19.1
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.19.1 [COLOR="Red"]root=/dev/hda2[/COLOR] ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.19.1
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.19.1 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.19.1 [COLOR="Red"]root=/dev/hda2[/COLOR] ro single
initrd		/boot/initrd.img-2.6.19.1
boot
```

check if your [COLOR="Red"]root=/dev/hdxX[/COLOR] in menu.lst is pointing to the right device in your fstab... mine wasn't, I don't know if that was clear... but my root partition is /dev/hda2, and in menu.lst the root partition was /dev/hda5

ps: sorry for my english :lolflag:

---

