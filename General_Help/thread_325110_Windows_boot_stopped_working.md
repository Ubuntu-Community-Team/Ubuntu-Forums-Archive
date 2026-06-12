---
title: "Windows boot stopped working?"
date: 2006-12-25
forum: General Help
---

### Post by BetaMaster on 2006-12-25
Hey, I usually use Windows, and have recently upgraded to Vista. A week back or so, I installed Ubuntu again, and have been using it since. I wanted to go back into Windows today to use Photoshop, but I can't get it to work!

I choose Vista/Longhorn from GRUB, and it shows a black screen, then the Windows loading screen shows up.

Then, nothing. Black screen again. Nothing else happens. I let it sit for a half hour, just in case, but nothing.

I haven't used it since I installed Ubuntu (and GRUB).
Is there a setting I need to do for GRUB to boot Vista?

What's the problem here?

Any help would be appreciated.

---

### Post by dbbolton on 2006-12-25
can you mount windows from ubuntu ?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)


(to see if that filesystem is corrupt)

---

### Post by BetaMaster on 2006-12-25
Well, I have it mounted through ntfs-3g, and it does work. I just tried umounting and remounting it, and it still works - though I get an error, strangely enough.
> sven@sven-desktop:~$ sudo mount -a
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Failed to mount '/dev/hda1': Device or resource busy
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

I think that might be because ntfs-3g is mounting the NTFS disk on its own though.
Hmm, I only have read permissions on that drive, I'm checking right now.

I really don't have any idea what's wrong. I can't see how the filesystem was corrupted, when I haven't touched it in over a week, and it worked fine last time.

Should I try umounting it next time before I shut down or something? Could the drive be getting errored out by Ubuntu?

---

