---
title: "Today's updates (7 Oct. 2015) broke audio and other things"
date: 2015-10-07
forum: General Help
---

### Post by LLigetfa on 2015-10-07
I did not pay close attention to what new bits came today but after the reboot, the audio no longer works and I cannot shutdown using the DE UI.  The soft touch buttons above the keyboard give mixed results.  Sometimes an OSD overlay shows but the mute button never changes from red to green.  The volume up down don't work.  No sound at all.  If I launch sound control panel, I cannot close it.

Also starting today, Chrome on the mail.live.com site keeps popping up Flash Player warnings.  Not sure if it is related.

This is ubuntu 14.04 on an HP EliteBook 8540w.

How can I know what new bits broke this and can I rollback the updates?

---

### Post by LLigetfa on 2015-10-07
After checking the log with tail -n25 /var/log/apt/history.log I see the following were applied today.  Sorry for the wall of text, not sure where the lines should break.
> Start-Date: 2015-10-07  09:20:58
Commandline: aptdaemon role='role-commit-packages' sender=':1.102'
Install: linux-image-extra-3.13.0-66-generic:amd64 (3.13.0-66.107), linux-image-3.13.0-66-generic:amd64 (3.13.0-66.107), linux-headers-3.13.0-66:amd64 (3.13.0-66.107), linux-headers-3.13.0-66-generic:amd64 (3.13.0-66.107)
Upgrade: libsystemd-login0:amd64 (204-5ubuntu20.14, 204-5ubuntu20.15), linux-headers-generic:amd64 (3.13.0.65.71, 3.13.0.66.72), systemd-services:amd64 (204-5ubuntu20.14, 204-5ubuntu20.15), libsystemd-daemon0:amd64 (204-5ubuntu20.14, 204-5ubuntu20.15), libgudev-1.0-0:amd64 (204-5ubuntu20.14, 204-5ubuntu20.15), libpam-systemd:amd64 (204-5ubuntu20.14, 204-5ubuntu20.15), udev:amd64 (204-5ubuntu20.14, 204-5ubuntu20.15), gir1.2-gudev-1.0:amd64 (204-5ubuntu20.14, 204-5ubuntu20.15), libspice-server1:amd64 (0.12.4-0nocelt2ubuntu1.1, 0.12.4-0nocelt2ubuntu1.2), libudev1:amd64 (204-5ubuntu20.14, 204-5ubuntu20.15), libudev1:i386 (204-5ubuntu20.14, 204-5ubuntu20.15), libsystemd-journal0:amd64 (204-5ubuntu20.14, 204-5ubuntu20.15), linux-libc-dev:amd64 (3.13.0-65.106, 3.13.0-66.107), linux-image-generic:amd64 (3.13.0.65.71, 3.13.0.66.72), linux-generic:amd64 (3.13.0.65.71, 3.13.0.66.72)
End-Date: 2015-10-07  09:23:20

---

### Post by howefield on 2015-10-07
There are several threads on the forum today with the same/similar issue, and most likely a fix will be forth coming quickly.

In the meantime can you boot in to the previously working kernel ?

---

### Post by LLigetfa on 2015-10-07
Thanks for advising me that this is a known issue.  I hope there is a fix soon but since I am not quite dead in the water I can probably wait for it.
I don't know how to boot to the previous kernel but willing to give it a go with a bit of coaching.  Am I right in guessing there is an option that is revealed by holding down the shift button on boot?

---

### Post by howefield on 2015-10-07
> **LLigetfa said:**
> I don't know how to boot to the previous kernel but willing to give it a go with a bit of coaching.  Am I right in guessing there is an option that is revealed by holding down the shift button on boot?

That's it, switch on and hold the shift key, there should be an advanced options in the menu which will list the available kernels to boot from, just select the second to newest. I can't remember exactly how the boot menu looks in 14.04 but if you can bring it up, the options should be obvious.

---

### Post by mbott on 2015-10-07
Today's 14.04 update totally killed my system. So. took the opportunity to jump to 15.04.  I'm not going back.

-- 
Mike

---

### Post by LLigetfa on 2015-10-09
OK, so I've booted on the previous kernel and since then have been offered a bunch of updates.  How would I know if any of these updates are to address the issue I am facing?  Is it reasonable to think it would be fixed so soon?

I put off the updates yesterday and today there are a bunch more including 3.13.0 kernel bits.  Are these bits only being offered because I am running the previous kernel or are they re-released bits?  Are the fixes required to the kernel or to other dependent modules?

---

### Post by howefield on 2015-10-09
The fixes were released to -proposed on the 7th, so what you are seeing should be the updated linux-image-3.13.0-66-generic_3.13.0-66.108_amd64.deb and associated packages.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655)

---

### Post by LLigetfa on 2015-10-09
The updates fixed everything.

Thanks a lot!

---

### Post by howefield on 2015-10-10
Terrific, you now have a choice.. to keep -proposed enabled or not :)

---

### Post by mbott on 2015-10-10
> **mbott said:**
> Today's 14.04 update totally killed my system. So. took the opportunity to jump to 15.04.  I'm not going back.


I went back to 14.04 after all. Prefer at least one of my systems on an LTS, so I restored a previous image (Clonezilla is your friend), deselected -proposed, and allowed the updates to catch up.

-- 
Mike

---

### Post by LLigetfa on 2015-10-10
> **howefield said:**
> Terrific, you now have a choice.. to keep -proposed enabled or not :)

I forgot that I had that selected.  I was having issues with my NVIDIA card and thought it was the drivers so was desperate enough to get on the edge.  The video issues just kept getting worse and it turned out to be a hardware issue.  Replaced the card and all was well.

---

