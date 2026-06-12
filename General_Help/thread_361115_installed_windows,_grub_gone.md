---
title: "installed windows, grub gone"
date: 2007-02-14
forum: General Help
---

### Post by gaillard on 2007-02-14
I tried the howto here
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=installed+windows+lost+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=installed+windows+lost+grub)

and when I restarted boom windows just automatically booted up and no grub.

I have ubuntu on one drive and I installed windows on my second, thats when I lost the grub.  Is there anything I can do!?

---

### Post by gaillard on 2007-02-14
nevermind I entered a command wrong on the howto, HOWEVER

When I tried to boot ubuntu I got some crazy box error or something, and it left me on a screen not even a terminal just black with garbage writing.  I am just going to reinstall ubuntu.  Thanks anyways!

---

### Post by housam on 2007-02-14
Or you can [restore grub]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by predator on 2007-02-14
It's possible you have corrupted your kernel in some way, which would either require a lot of stuffing around, or a reinstall.. 

Or if you're lucky it's just grub record is stuffed.. you could also try the following (borrowed from a howto somewhere) .. It's worked for me..

boot into the setup CD.. run konsole... type: 'sudo grub'

when the prompt comes up.. 

'find /boot/grub/stage1'
then it should print out something like (hd1,1) - in my case 2nd partition on 2nd drive
type 'root (hd1,1)' (or whatever was displayed above, or where main /boot/ partition is stored)
type 'setup (hd0)'  -- your hard disk 1, 1st partition.. or where windows sits

it should say 'installing grub, etc'..

then type 'quit'

and reboot. If you're lucky you get grub.. if not, you reinstall :p (or look at other options)

---

