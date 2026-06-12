---
title: "Can't boot into Ubuntu or Live CD"
date: 2008-06-08
forum: General Help
---

### Post by sparkguitar05 on 2008-06-08
I installed Ubuntu a few months ago and have been running it alongside Windows ever since.  I do most of my work in Ubuntu and use Windows for the things Linux doesn't handle very well (mostly video editing).

One day I started up my computer and Ubuntu wouldn't load.  It got past the GRUB screen and said "Starting up" but it never started up.  I tried this multiple times and let it load for an hour one time and it never managed to boot up.

Then I thought, "If Ubuntu isn't going to work I'll just pop in the live CD and transfer all my files over to Windows."  So I popped in the live CD for Hardy.  I got to the main screen and selected "try Ubuntu without any change to your computer".  Then I was greeted for a flashing cursor for an hour and a half.  Ubuntu refused to boot from the live CD.  I finally gave up and put in the live CD for Gusty.  And guess what?  That one didn't work either!  I got to the main screen with the options and when I told it to boot into the live CD it wouldn't load.

I don't know what to do now.  Most of my files are on my Ubuntu partition and I have no way to access it.

Someone please help me! :(

---

### Post by overdrank on 2008-06-09
> **sparkguitar05 said:**
> I installed Ubuntu a few months ago and have been running it alongside Windows ever since.  I do most of my work in Ubuntu and use Windows for the things Linux doesn't handle very well (mostly video editing).

One day I started up my computer and Ubuntu wouldn't load.  It got past the GRUB screen and said "Starting up" but it never started up.  I tried this multiple times and let it load for an hour one time and it never managed to boot up.

Then I thought, "If Ubuntu isn't going to work I'll just pop in the live CD and transfer all my files over to Windows."  So I popped in the live CD for Hardy.  I got to the main screen and selected "try Ubuntu without any change to your computer".  Then I was greeted for a flashing cursor for an hour and a half.  Ubuntu refused to boot from the live CD.  I finally gave up and put in the live CD for Gusty.  And guess what?  That one didn't work either!  I got to the main screen with the options and when I told it to boot into the live CD it wouldn't load.

I don't know what to do now.  Most of my files are on my Ubuntu partition and I have no way to access it.

Someone please help me! :(

HI and have you tried booting into recovery mode from the grub? You could try from the live cd again and press F6 to edit and remove the quiet splash so you could see any errors that occur.

---

### Post by sparkguitar05 on 2008-06-09
Thanks.  I'll try that and get back to you.

---

### Post by sparkguitar05 on 2008-06-09
> **overdrank said:**
> HI and have you tried booting into recovery mode from the grub? You could try from the live cd again and press F6 to edit and remove the quiet splash so you could see any errors that occur.

I tried booting into recovery mode from the grub.  It stopped when it got to "checking if image is initramfs... it is".

Then I tried booting from the live CD and removing quite splash.  It stopped booting when it got to the exact same message.

Any ideas?

---

### Post by sparkguitar05 on 2008-06-09
*bump*

Anyone?  I need my files back!

---

### Post by cariboo on 2008-06-09
Use this program to access your linux files from windows. I use it in Vista and it works wel.

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Jim

---

### Post by sparkguitar05 on 2008-06-09
Didn't work.  I have my / and my /home directories on separate partitions.  It could access the / directory, but not the /home directory (which contains the files I need).

Anyone else?

---

### Post by Habbit on 2008-06-09
If your /home is in a ReiserFS partition, as mine is, that app won't work, as it only reads ext2/3 volumes. Try [YaREG]("http://yareg.akucom.de/").

WRT Ubuntu itself. You might want to try to:
[LIST]
[*]remove any hardware that you have recently plugged, like a new USB printer or mouse.
[*]boot your Ubuntu installation in "recovery mode" (an option in the GRUB menu) or at the very least without the "quiet" and "splash" options in the kernel command line. This will show you the kernel messages, and among the last of them, there might be a clue so as to what causes the lookup. Hint: look for the words "Oops" and "PANIC", or for repeating messages like "hda1: retrying read from block #x - read failure".
[*]boot from a live CD from another distro. Maybe their kernel will not have the offending component (if it's in the kernel).
[*]check your HD - you might think that even if your HD has gone to the dogs, booting from the CD shall be fine, but the CD tries to activate the swap partitions it finds, which might bork the system.
[*]check your memory - if you have a lot of memory (> 1GB), you may not hit the problem on Windows until you open a lot of programs because it uses free memory as cache less aggressively than Linux.
[/LIST]

---

### Post by sparkguitar05 on 2008-06-09
My /home directory is in an ext3 partition.

I tried recovery mode and posted my results a few posts above this one.  Can you scroll up and check that out?  That probably tells what's going on, but I don't know what it means.

Thanks.

---

### Post by Gannon8 on 2008-06-09
Use ext2ifs ([http://www.fs-driver.org/](http://www.fs-driver.org/)). After installing, go to Control Panel, click on the "IFS Driver" icon, and mount your /home partition. Then go to My computer and look for whatever drive letter you assigned your /home partition.

---

### Post by sparkguitar05 on 2008-06-09
Thanks.  That worked great.

Can anyone help me boot into Ubuntu in case I want to use it again?

---

