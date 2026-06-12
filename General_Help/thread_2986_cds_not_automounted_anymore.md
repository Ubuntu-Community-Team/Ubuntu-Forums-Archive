---
title: "cds not automounted anymore"
date: 2004-11-02
forum: General Help
---

### Post by qstone on 2004-11-02
Hi there. I'm having fun with ubuntu for one week now. Until yesterday I had icons automagically popping on my desktop every time I inserted a CD, and the right application was launched.
Now I have to mount the cds manually, and I can't find how to re-enable that automount feature.
dmesg doesn't display anything about my cd drives (/dev/hdc and /dev/hdd).
lshal displays the version number, waits a couple of seconds, then finishes without showing anything, or crashes (I don't have the error message here right now, I can post it if it helps).

Speaking about the automount, I can't mount my usb thumb drive at all... It says the device /dev/sda1 does not exist ?!?

---

### Post by mercurus on 2004-11-02
[QUOTE=qstone]Until yesterday I had icons automagically popping on my desktop every time I inserted a CD, and the right application was launched. Now I have to mount the cds manually, and I can't find how to re-enable that automount feature.[/QUOTE]

Have a look in Computer,Desktop Preferences, Removeable Storage. Ensure the three checkboxes are ticked for the three different media types, and make sure that the commands the mounter is executing are valid. (ie. open a terminal and test them manually)

> Speaking about the automount, I can't mount my usb thumb drive at all... It says the device /dev/sda1 does not exist ?!?

I just tried to use my thumbdrive (its built into a watch) and it worked perfectly without any intervention from me.

In the past I've discovered that it might be necessary to have the usb-storage module loaded before the device is inserted. Also, check your kernel includes scsi disk support, as it is often required to mount USB drives.

Otherwise, can you:
- reboot your system
- login as normal
- when everything is loaded, insert the USB drive
- if nothing happens or you get errors, then remove the USB drive
Could you please copy and paste the log starting from when the device is inserted, and ending when it is removed ?

Finally, make sure all your gnome-vfs packages are up to date with apt-get and check that the ubuntu-desktop virtual package is installed.

Cheers
mercurus

---

### Post by qstone on 2004-11-02
Thanks mercurus, I finally get my CDs mounted.
The 3 checkboxes were ticked. I tried to insert various discs :
- audio cd -> the cd player is run and plays my music fine,
- blank cd -> launches nautilus burn app,
- cd-rom -> nothing happens. Manual mount works fine and adds icon to the desktop.
The problem with cd-roms was in the /media/ directory. Last week there were 2 subdirs (cdrom0 and cdrom1, my dvd-reader, and cd-burner), plus 1 symbolic link (cdrom -> cdrom0).  Today I had only the link (?). re-creating the dirs instantly repaired the problem.
I'm investigating on what might have caused the directories to disappear suddently, I'll post a bug if I find something.

And now, for the usb thumbdrive : it still doesn't work. I checked I'm up to date (well, my PC is...), and I have all the packages you mentioned. Here is the log extract :
-----(first try)-----
Nov  2 18:42:23 localhost kernel: usb 3-2: new full speed USB device using address 2
Nov  2 18:42:23 localhost kernel: SCSI subsystem initialized
Nov  2 18:42:23 localhost kernel: Initializing USB Mass Storage driver...
Nov  2 18:42:25 localhost kernel: usb 3-2: USB disconnect, address 2
Nov  2 18:42:25 localhost usb.agent[11933]:      usb-storage: loaded successfully
Nov  2 18:42:25 localhost kernel: usb-storage: probe of 3-2:1.0 failed with error -1
Nov  2 18:42:25 localhost kernel: usbcore: registered new driver usb-storage
Nov  2 18:42:25 localhost kernel: USB Mass Storage support registered.
Nov  2 18:43:52 localhost kernel: usb 3-2: new full speed USB device using address 3
-----(end of first try)-----

-----(second try)-----
Nov  2 18:43:57 localhost kernel: usb 3-2: control timeout on ep0out
Nov  2 18:44:02 localhost kernel: usb 3-2: control timeout on ep0out
Nov  2 18:44:03 localhost kernel: usb 3-2: device not accepting address 3, error -110
Nov  2 18:44:03 localhost kernel: usb 3-2: new full speed USB device using address 4
Nov  2 18:44:08 localhost kernel: usb 3-2: control timeout on ep0out
Nov  2 18:44:13 localhost kernel: usb 3-2: control timeout on ep0out
Nov  2 18:44:13 localhost kernel: usb 3-2: device not accepting address 4, error -110
-----(end of second try)-----


I hope it will look obvious for someone, for me it's definitely not ;)

---

### Post by mercurus on 2004-11-03
[QUOTE=qstone]Thanks mercurus, I finally get my CDs mounted.
The 3 checkboxes were ticked. I tried to insert various discs :
- audio cd -> the cd player is run and plays my music fine,
- blank cd -> launches nautilus burn app,
- cd-rom -> nothing happens. Manual mount works fine and adds icon to the desktop.
The problem with cd-roms was in the /media/ directory. Last week there were 2 subdirs (cdrom0 and cdrom1, my dvd-reader, and cd-burner), plus 1 symbolic link (cdrom -> cdrom0).  Today I had only the link (?). re-creating the dirs instantly repaired the problem.
I'm investigating on what might have caused the directories to disappear suddently, I'll post a bug if I find something.[/quote]

That **is** curious ... If you want CDs to mount and run automatically, there is an auto-run feature on the same setup screen, although I haven't tested it - because it annoys me intensely ! :p

> And now, for the usb thumbdrive : it still doesn't work. I checked I'm up to date (well, my PC is...), and I have all the packages you mentioned. Here is the log extract:
-snip-
I hope it will look obvious for someone, for me it's definitely not ;)

I ran a google search for the errors you listed and low and behold, you appear to have struck a kernel bug.
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=124027](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=124027)
There is a patch available on that page, but I have no idea how effective or dubious it may be. If you can wait, I'd leave it until a new kernel package is released by the Ubuntu developers. If not, grab the latest kernel source and recompile it using the Ubuntu Kernel-HOWTO and hopefully it will resolve the issue. If not, try and compile another kernel with the patch they suggest above.

Cheers
mercurus

---

### Post by qstone on 2004-11-03
> That is curious ... If you want CDs to mount and run automatically, there is an auto-run feature on the same setup screen
That's what I use, but was broken because of the directories that disappeared... I'm really curious to find out what may have caused this !!!
> I ran a google search for the errors you listed and low and behold, you appear to have struck a kernel bug.
](*,)  why didn't I tried a google search earlier ?!? I'm used to do that...
I'm familiar with kernel patching and re-compiling, but I think I'll wait for the official one (at least until it really annoys me ;) . 

Well, thank you a lot for helping me, mercurus  :razz:
See ya !

---

