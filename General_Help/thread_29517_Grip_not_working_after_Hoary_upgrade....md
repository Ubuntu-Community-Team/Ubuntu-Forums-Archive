---
title: "Grip not working after Hoary upgrade..."
date: 2005-04-24
forum: General Help
---

### Post by BigRod on 2005-04-24
I upgraded to Hoary 2 days ago and now Grip can no longer initialize my CD Rom drive.  I am not sure what to try.  The drive appears to be mounted just fine and I can open CDs in Nautilus.

I had it configured to use /dev/cdrom, but the first time I started it up it said "Unable to initialize /dev/cdrom."  So, I tried changing it to /dev/cdrom0 and /dev/cdrom1 and got the same message.  Then, I tried /media/cdrom, the mountpoint, and I don't get the message but it still won't read the cd.  I tried reinstalling grip as well and that didn't work either.

If anyone has an idea what might be happening, I'd appreciate the help.

---

### Post by BigRod on 2005-04-24
Anybody?

How can I remove Grip completely and reinstall it?

---

### Post by BigRod on 2005-04-24
Anyone at least know another application that I can install to rip MP3s that works well?

---

### Post by Gary Powers on 2005-04-24
Have you looked at Gnome Baker?  I've used it to burn CD's recently and it worked well .... unfortunately I'm on a Mac right now and cant' check it out for you.

Gary

---

### Post by tread on 2005-04-25
Sound Juicer Cd Ripper is what you want ..

---

### Post by BigRod on 2005-04-25
Gnome Baker is just for burning discs, right?

And Sound Juicer can only do Ogg or Flac (or wav), and my mp3 player doesn't support either of them.

Anyhow, I discovered what happened.  For some reason, when I upgraded it changed my cdrom device names to /dev/hdc and /dev/hdd instead of the traditional /dev/cdrom0 and /dev/cdrom1.  The funny thing is that it didn't change the mountpoint names, they are still /media/cdrom0 and /media/cdrom1.  Whatever, it works now :).

---

