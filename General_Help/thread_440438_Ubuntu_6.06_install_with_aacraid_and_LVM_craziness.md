---
title: "Ubuntu 6.06 install with aacraid and LVM craziness (sd_mod's fault?)"
date: 2007-05-11
forum: General Help
---

### Post by volumen1 on 2007-05-11
So, here's the deal.  I'm a Gentoo user who is playing around with Ubuntu and I've hit a weird problem.  The servers that I've installed 6.06 on have Adaptec SAS 4805 raid controllers.  This is, I believe, handled by the aacraid module.

During the install, everything works just fine, the installer only sees /dev/sda and I can set that up how I like it.  I setup /, /boot and swap and then use the rest of the RAID1 mirror (that I created using the Adaptec BIOS utility) as a big LVM volume.

Then I partition /tmp, /usr, /opt, /home and so on,  out of that LVM volume.  This all works fine as well.  But, once I complete the installation and reboot I hit a weird issue.  /dev/sda, /dev/sdb and /dev/sdc are all created.  It's my guess that /dev/sda is my logical drive (the RAID1 mirror) and sdb/sdc are the actual physical disks that make up the array.  I say that because both sdb and sdc have unpartitioned space on them and they are identical.  Whereas sda doesn't show that unpartitioned space and it's the oddball.

Why is this a problem, you might ask.  Well, the lvm.conf file has a pretty broad filter= line and it actually finds PVs on all 3 disks.  And, what's worse, it seems to randomly write to either sda, sdb or sdc.  So, after a short while, I'm in a rough spot with filesystem corruption.

So, I'm looking for a good way to fix this.  So far, I've tried to add "blacklist sd_mod" to /etc/modprobe.d/blacklists to prevent sd_mod from loading.  But, I'm not sure if this the correct way to solve this problem.  If it is, it didn't work.  sd_mod still got loaded on a reboot.

I suppose I could also just install Ubuntu and then boot into a LiveCD environment and edit my lvm.conf to only include /dev/sda, but this feels kludgy.

Has anyone else seen this problem?  Any advice?

Thanks,

shane

---

### Post by volumen1 on 2007-05-21
Hmm... I'm a little surprised that I didn't get any responses to this.  If this had been the Gentoo forums, I'd be choking on replies right now.  Anyway, we started fresh with 7.04 and this behavior went away.  It must have been related to the kernel used for the 6.06 version.

---

