---
title: "Can't boot into Ubuntu"
date: 2007-03-16
forum: General Help
---

### Post by royrules22 on 2007-03-16
Right, this is a problem. So I had installed Beryl and was happily messing around enjoying the effects when a key combo suddenly logged me out. I logged right back in and there were no problems. Somehow I keep triggering this combo (I believe Shift was common to it all). It could also be a mouse click since I can't turn off the stupid touch pad and I tend to accidently touch/tap it. In any case this happened atleast four times. The last time the little Ubuntu box that shows all the programs that are loading was stuck on the screen, and it didn't load Beryl Manager. However everything still worked. So I manually started Beryl screen manager and everything was fine. Except for that box. Still there. Since it was annoying I tried restarting. It freezes. I end up doing a hard shutdown and start up.

That's when the problem occured. Basically during the bootup sequence right when the bar is almost full it freezes and this line comes across the screen. After a few seconds another line appears. And then it stays like that, leaving me no option but to turn off by using the power button. 

To illustrate exactly how it looks like here are two pictures:
[http://img.photobucket.com/albums/v406/royrules22/DSC01569.jpg](http://img.photobucket.com/albums/v406/royrules22/DSC01569.jpg)
[http://img.photobucket.com/albums/v406/royrules22/DSC01568.jpg](http://img.photobucket.com/albums/v406/royrules22/DSC01568.jpg)
And a YouTube [video showing]("http://www.youtube.com/watch?v=BQCc_P9RlBs") what happens during bootup. 

I'm trying to get it back up without having to reinstall. I tried my best searching for this topic already but I can't find any so sorry if I missed it.

Thanks.

---

### Post by scxtt on 2007-03-16
i get that too ... i edit my grub entry to use "nosplash", i'd rather see what it's doing during boot than watch a bar anyway :p ...

---

### Post by royrules22 on 2007-03-16
I can't quite edit GRUB without getting into Ubuntu unless there is a way to do it via Windows..

---

### Post by Adramelech on 2007-03-16
use the live cd to boot and edit the file, or use ext2 drivers to see your linux partition from windows

---

### Post by scxtt on 2007-03-16
you can edit it (albeit not save it) from the grub menu before the OS tries to load, then once you're in actually edit /boot/grub/menu.lst ...

---

### Post by royrules22 on 2007-03-16
I think I may have found the problem. Step by step what I did.

1) I downloaded [Ext2 Installable File System For Windows]("http://www.fs-driver.org/index.html")
2) I installed it and set my Linux drive to H:
3) It gives me an error saying that I should reformat it (i.e. it doesn't read it as an ext2 FS).
4) [The FAQ ]("http://www.fs-driver.org/troubleshoot.html")says I should run the mountdiag diagnosis tool, which I do.
5) mountdaig says:
[QUOTE=mountdiag]The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.10 software did not
mount it because there is at least one incompat feature flag set. The Ext2
IFS software does not implement:
* needs_recovery *
Here we have an Ext3 file system which has transactions left in its journal. A
pure Ext2 driver must not access such a volume which is in that state (to
prevent data loss!).
You may solve it by mounting it on Linux (which has a kernel with Ext3
support). Be sure that you cleanly dismount it, before you shutdown Linux.
After that the Ext2 IFS software should be able to access the volume.[/QUOTE]

Apparently something about needing to recover it. Whatever it is, it's not good (or it seems). I have no clue what to do next since I have no experience with file systems and what not.

---

### Post by scxtt on 2007-03-16
uh, i think you're barking up the wrong tree ... there's a difference b/t ext2 and ext3 and you seem to be using some ext2 tool - again you DON'T need to edit the file to make ubuntu boot, you can do that later ...

i'd reboot, hit "escape" at the grub menu (if required), move the cursor over your kernel entry, hit "e" and preface "splash" w/ "no" (= "nosplash"), hit enter, then hit "b" ...

---

### Post by royrules22 on 2007-03-16
I think I figured this out. Here's a [vid of the bootup]("http://www.youtube.com/watch?v=Bn3GD0JxsFA") if you want to have a looksee.

In any case it's a stupid error in my xorg.conf file (introduced by the fact that I messed up when trying to stop my touchpad from recognizing taps). I guess it should be easy to fix -> edit the file. However when I tried to do *sudo vi xorg.conf* and I edited the file to remove the code and I tried to quit vi by using :q it said something to the extent of "nothing to write", so I tried using :q! and it quit vi. Apparently however it doesn't write. 

So any help on editing xorg.conf via vi or whatever? I'm more of an emacs person (and I've only used the GUI version.. i'm not even sure if there is a text based emacs).

Also when I was on the command line I got this message:
[http://img.photobucket.com/albums/v406/royrules22/DSC01571.jpg](http://img.photobucket.com/albums/v406/royrules22/DSC01571.jpg)

What's that supposed to be?

Edit- According to Google :wq! is how you write and quit. Off to do that now. Still wondering what that second message is..

Edit Again: Got it! Thanks for telling me how to do that no splash thing. Now if I can just figure out why I'm being logged out.. It definatly involves the shift key, and I think it has something to do with Beryl..

---

