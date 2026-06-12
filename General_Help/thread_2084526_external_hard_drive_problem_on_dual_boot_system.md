---
title: "external hard drive problem on dual boot system"
date: 2012-11-15
forum: General Help
---

### Post by bertmung on 2012-11-15
I recently installed 12.10 on a new machine using the windows installer.

Occaisionally I use Windows. There's a web based audio chat application that doesn't work in Ubuntu. Or I leave during the boot process and the system boots up in the default (windows)

I started having problems with usb storage devices becoming read only when returning to Ubuntu from Windows. At first I could solve them by going back into Windows and changing the removal policy. After changing to policy to requiring use of the remove device safely button everything would be fine.

I tried to do that today and windows can't even read the device. It knows the device is there and lets me change the policies. It can't read any data. Changing the policies doesn't have any effect when i return to Ubuntu.

What's my next step?

---

### Post by bertmung on 2012-11-15
I'm marking this as solved.

Turns out that switching between windows and ubuntu was probably a red herring. The machine had suddenly shut down while I was dealing with the keyboard cable not being plugged all the way in. I probably leaned on the button accidently.

I ran reiserfsck.  See [http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html](http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html) for how I did it.

I was surprised at how helpful the man page was for reiserfsck.

---

