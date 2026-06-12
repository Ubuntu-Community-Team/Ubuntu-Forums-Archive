---
title: "I don't know where this belongs, but it's kernel problems."
date: 2006-10-17
forum: General Help
---

### Post by sktfeelsdapper on 2006-10-17
So, I broke Ubuntu.
And I decided to myself that I would download and burn Kubuntu to give it a try, and everything seemed fine.

But I get a mess of errors when I do anything.
For starters I can't mount my second hardrive, or look at my disks in System settings > Disk & Filesystems

The following error comes up:
The module Disk & Filesystems could not be loaded.

The diagnositics is:

An Error occured during your last KDE upgrade leaving an ophaned control module.
You have old third party modules lying around.

Which doesn't make sense, I also can't seem to mount my second hardrive because of a bad fs type, even though I know for sure it's ext3.

And that's not all!

This happens when I go to use Kate.
skt@skt-desktop:~$ kate
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin(

Oh and it mentions something about the xserver, which I've uninstalled and reinstalled and still get the same problems.

Bad disc? Did I do something wrong? I just burnt the cd, and installed it like I have with Ubuntu, Xubuntu and others. What's going on?](*,)

---

### Post by ajgreeny on 2006-10-17
I've always got the error message you show when starting kate in the terminal, and most other kde programs throw up similar error messages for some reason related to xsession, I think.  My ~/xsession-errors file is littered with similar errors, but it doesn't seem to make any difference to how it all works and I just ignore them.

I googled for any info I could find on this and got a lot of useless references which led me nowhere.  Everything works great, somas I say, I just ignore them.

Your other problem is more puzzling but how are you trying to mount the other disk, and what is on it?  The only time I have had problems was with mounting Fedora core 5, which was not on a primary partition but on a LVM.  Have a look at
[http://ubuntuforums.org/showthread.php?t=179128](http://ubuntuforums.org/showthread.php?t=179128)
for further info on how that was sorted out.  I didn't like Fedora much anyway so kame back to Ubuntu with Kubuntu-desktop added afterwards - GREAT!

---

### Post by rbmorse on 2006-10-18
THe input device 168 error is simply X trying to load a Wacom tablet and not finding one. It's a benign error.

---

