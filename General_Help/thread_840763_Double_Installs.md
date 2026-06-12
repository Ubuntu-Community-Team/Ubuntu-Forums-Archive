---
title: "Double Installs?"
date: 2008-06-25
forum: General Help
---

### Post by Minkerton on 2008-06-25
So I'm completely new to Linux, and thought Ubuntu would be a great place to start.. but I think I've messed up pretty badly already.

I have WinXP Pro SP2 installed on one drive.. and installed Heron on my other drive.  Things went flawlessly.

I started to tinker around and had to do a reboot, now it won't boot back into Ubuntu.  So I thought, why not just start over, didn't take too long in the first place.

Drop the CD back in, and reinstalled.. or so I thought.

Now I have 2 installs of Ubuntu and my XP install.
I think I've partitioned the one drive twice now.

What I want to do it completely remove both Ubuntu installs and start over.

Any help is greatly appreciated.  Thanks in advance!

---

### Post by VMC on 2008-06-25
> **Minkerton said:**
> So I'm completely new to Linux, and thought Ubuntu would be a great place to start.. but I think I've messed up pretty badly already.

I have WinXP Pro SP2 installed on one drive.. and installed Heron on my other drive.  Things went flawlessly.

I started to tinker around and had to do a reboot, now it won't boot back into Ubuntu.  So I thought, why not just start over, didn't take too long in the first place.

Drop the CD back in, and reinstalled.. or so I thought.

Now I have 2 installs of Ubuntu and my XP install.
I think I've partitioned the one drive twice now.

What I want to do it completely remove both Ubuntu installs and start over.

Any help is greatly appreciated.  Thanks in advance!

Boot from lice cd and from a Terminal type "gparted"

It will bring up a gui partition manager.

Looke to the far right and make sure your dealing with the correct drive.
Also there should be some Ext2 or Ext3 and a swp partition. You can delete
all of those.

---

### Post by Minkerton on 2008-06-25
Thank you for the info.

I actually just managed to find that out for myself, but downloaded the Gparted Live CD and booted from that.

Everything is back and working again.

Turns out the culprit was the ATI restricted drivers, kept causing the first install to hang.  Not going to bother installing them this time around.

---

