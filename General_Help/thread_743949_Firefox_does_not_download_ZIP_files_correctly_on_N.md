---
title: "Firefox does not download ZIP files correctly on NTFS drive"
date: 2008-04-03
forum: General Help
---

### Post by bixejo on 2008-04-03
I've installed a dual boot Ubuntu 7.10/Win-XP system on my laptop. I can see my XP partition from Ubuntu and can create/write/read/delete files on the NTFS partition without apparent problems.

However, whenever I try to download ZIP files on the NTFS drive with Firefox, they get corrupted (missing parts, and unzip -t reports problems.) I get no problems when I download them on the Ubuntu ext3 partition and moving them to the NTFS drive afterwards.

Is this a known issue? Is there anything I can do to fix this?

My Linux OS is an Ubuntu 7.10 x86_64. More info follows:

> 
bixejo@colmena:~$ dpkg -l | grep -i firefox
ii firefox 2.0.0.13+1nobinonly-0ubuntu0.7.10 lightweight web browser based on Mozilla
ii firefox-gnome-support 2.0.0.13+1nobinonly-0ubuntu0.7.10 Support for Gnome in Mozilla Firefox
ii mozilla-firefox-locale-en-gb 2.0.0.7+1-0ubuntu2 Mozilla Firefox English language/region pack
ii mozilla-firefox-locale-es-ar 2.0.0.7+1-0ubuntu2 Mozilla Firefox Spanish; Castilian language/
ii mozilla-firefox-locale-es-es 2.0.0.7+1-0ubuntu2 Mozilla Firefox Spanish; Castilian language/
ii ubufox 0.4~beta1-0ubuntu6 modifications for ubuntu firefox (default) i
bixejo@colmena:~$ uname -a
Linux colmena 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
And for the NTFS support:

> 
bixejo@colmena:~$ dpkg -l | grep -i ntfs
ii libntfs-3g12 1:1.913-2ubuntu1 ntfs-3g filesystem in userspace (FUSE) libra
ii ntfs-3g 1:1.913-2ubuntu1 read-write NTFS driver for FUSE
Any help will be welcome.
Regards and thank you in advance,

--Bixejo

---

### Post by -grubby on 2008-04-03
I have flagged this post to recieve more attention from other Unanswered post team members. I'm only posting this because it's required by the Firefox plugin in order to be flagged without error.

---

### Post by bixejo on 2008-04-04
Thank you nathan

---

