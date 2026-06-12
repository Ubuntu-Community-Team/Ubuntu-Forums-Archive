---
title: "Ubuntu ntfs-3g can't read Vista NTFS partition?"
date: 2007-10-22
forum: General Help
---

### Post by rev_b on 2007-10-22
Hello there.
My main OS is Ubuntu for over a year now, and I just kept a XP partiton on another hard disk for gaming. Ubuntu mounted the NTFS partition just fine, and XP saw all linux partitions with [http://www.fs-driver.org/](http://www.fs-driver.org/) so they got along just fine. I even have all my games installed on a ext3 partition.

Just for fun, I tried to upgrade XP to Vista. Of course, after the upgrade I was presented with a nice BSOD, so I just formatted the NTFS partition and did a clean install.

Problems: Ubuntu can't mount the Vista NTFS partition anymore. Gparted shows the NTFS partion, but it says it is unreadable (!) I just did a CHKDSK on Vista and it found no errors on the filesystem. The Ext2IFS driver also doesn't work in vista, it installs, but whenever I try to configure Linux partitions startinf IFS from the control panel, DEP prevents it from running. Just fantastic.

Did Vista introduced changes on NTFS that ntfs-3g can't read it anymore, or I'm missing something here?

Thanks.

---

### Post by scrooge_74 on 2007-10-22
Can't help you on this one since I don't have any need for Vista or XP at this point in time.  But I could bet you that MS did made some changes so as to make Linux fans life more difficult, they do that to everybody, they had to know about ntfs-3g, so it is logically to assume they were going to do something about it.

---

### Post by rev_b on 2007-10-22
So, time to reformat and install XP SP2 I guess... Vista is the worst OS I've seen in ages. Totally bloated, intrusive, disfunctional, problems with hardware detection and drivers and not compatible with most software 1 ou 2 years old!  I think even Windows ME was more tolerable... Aero? pfff... Compiz runs in circles around it and doesn't need a DX9 card.

As I said I only use windows for ocasional gaming - fortunately most of my favourite games have Linux ports . So I don't really need Vista. All my work/surfing/music/video/office/burning DVD's is done with Ubuntu that gets better and better with every release.

---

### Post by rev_b on 2007-10-22
To whom it may concern, it was able to mount Vista NTFS partition with force option.

 sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

it gives an error "$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile." but it works anyway.

---

