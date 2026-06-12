---
title: "separate /home partition"
date: 2008-05-06
forum: General Help
---

### Post by lattmau on 2008-05-06
I've read that having /home on a separate partition makes its easier to reinstall ubuntu b/c all your settings would be on the /home partition.  

How does that work?  

Say there are 2 partitions:
Partition 1: /
Partition 2: /home

When I reinstall ubuntu in Partition 1, does /home not get installed again because it detects that partition 2 already has one?

If that is so, what if I wanted to reinstall both / and /home?

---

### Post by timcredible on 2008-05-06
yes, it makes it much easier.  make sure the installer isn't set to re-format partition2, and make sure the mount point for partition2 is /home.  then, after a new install, go back and add your users back in.  make sure the UIDs match (UID is in the Advanced tab in the Users and Groups program).  Check to see what UID each user is before reinstalling, then make sure you add them back with the same UID.  If you just have 1 user, no need to do this, the system asks you for the first user during the install.  As always, though, it's best to make sure you have a backup of anything important before doing any of this.

---

### Post by twright on 2008-05-06
in the installer you need use manual mode and set the mountpoint for  Partition 2 as /home (and untick format)

i currently have 4 partitions

Partition 1 : /boot (ext3)
Partition 2 : /home (XFS)
Partition 3 : / (ReiserFS)
Partition 4 : swap

the advantages of using XFS and ReiserFS is that they are both lightning fast so i can access my data more quickly, but i use ext3 for /boot as it can be mounted more quickly so my computer takes less time to boot

---

### Post by az on 2008-05-06
> **lattmau said:**
> I've read that having /home on a separate partition makes its easier to reinstall ubuntu b/c all your settings would be on the /home partition.  


It's a lot quicker/easier/safer to just back up the setting you want to keep and get rid of the ones that may be causeing you trouble.  The settings themselves take up remarkably little disk space.  And backing up your important data to a different disk is *a lot* safer.

There is no real reason to use a separate home partition.

---

### Post by twright on 2008-05-06
you do need to backup as well but a separate home partition is useful if you multiboot or if you create a lot of stuff in /home it can stop the system working efficiently. i would love to be able to be able to back up daily/on the fly but as i cannot having a separate /home partition allows me to reinstall instantly without having to worry about loosing my data.

i can now from liveCD to everything working the way i want it in just 30 minutes (with windows i would still be trying to remember where i left my license code after that time)
> **az said:**
> It's a lot quicker/easier/safer to just back up the setting you want to keep and get rid of the ones that may be causeing you trouble.  The settings themselves take up remarkably little disk space.  And backing up your important data to a different disk is *a lot* safer.

There is no real reason to use a separate home partition.

---

### Post by zhanglini on 2008-05-06
You probably won't make the mistake I did --- make sure you either select /home in the drop down box or type in /home, instead of /Home.
I ended up with a /home (real one) and a /Home (fake one).  Unfortunately, the real one was in /, and the fake one was on a separate partition.
Confused?

---

### Post by Oldsoldier2003 on 2008-05-06
> **zhanglini said:**
> You probably won't make the mistake I did --- make sure you either select /home in the drop down box or type in /home, instead of /Home.
I ended up with a /home (real one) and a /Home (fake one).  Unfortunately, the real one was in /, and the fake one was on a separate partition.
Confused?

Heh, I bet that was a shocker. Simple fix though :)

---

### Post by Oldsoldier2003 on 2008-05-06
> **az said:**
> It's a lot quicker/easier/safer to just back up the setting you want to keep and get rid of the ones that may be causeing you trouble.  The settings themselves take up remarkably little disk space.  And backing up your important data to a different disk is *a lot* safer.

There is no real reason to use a separate home partition.

After falling for the separate home fad, I tend to agree with you az. Yes it was nice when I was beta testing Hardy and had to do a few reinstalls, but its not that big of a deal. People forget that you still have to install all the packages that go with all those pretty settings. In the end its the data that matters not the settings. 

I won't be using a separate home again on any of my future boxes.

---

