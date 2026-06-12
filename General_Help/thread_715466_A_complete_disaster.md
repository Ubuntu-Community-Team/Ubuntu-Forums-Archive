---
title: "A complete disaster"
date: 2008-03-04
forum: General Help
---

### Post by davidcaiazzo on 2008-03-04
Okay so my journey begins two days ago. I ran the update manager and had a few updates, sorry don't remember exactly what they were as I wasn't really paying much attention at the time. Anyway it alls go good I shutdown and go to bed. The next morning I turn my laptop on, IBM T60p intel core duo, and all the sudden the gnome key ring isn't working and everything is just going sideways. So I go online and read, and  read, and read and nothing seems to work. I pop out my ubuntu cd(alternate) and reinstall. My current setup at the time is root and home with a xfs filesystem under lvm with the boot partition as ext3 and my swap with 3 gigs. All goes well I update and restart and everything goes to hell again. Now it is the gnome-settings-daemon. I read all the posts on the forum, did a simple restart, edited a few files, install sdbus-x11, nothing works. So I format my whole computer, including my home partition, update again now gnome won't even start after a restart. So I download the regular cd format do away with lvm and have the normal setup. Update again and now I can't use apt, I get different errors each time, firefox, pidgin, a bunch of apps won't even start, they they are present they just immediately close. I have been using Ubuntu for three years now, and before that was using straight debian. I can't figure out what is going on. Can anybody help?

---

### Post by hhhhhx on 2008-03-04
wow, looks like you've got yourself a little mess there.:(  Have you tried installing from the alternate cd. also, just as a thought, i don't actually know, but maybe you've got a dead-ish HDD

---

### Post by davidcaiazzo on 2008-03-05
well I did a install from the alt cd a few times then the regular ubuntu cd. I have it working now but I formatted the whole thing, no separate partitions all in ext3. My system is running a big sluggish though. I hope my hdd isn't dying. But yeah I guess I will find out in a few days.

---

### Post by wieman01 on 2008-03-05
It sounds a bit like a failing HD or RAM if you ask me. I cannot explain what is happening... Very odd.

---

### Post by mozetti on 2008-03-05
Trying to inject a little humor here, but also serious:

They define "crazy" as doing the same thing repeatedly, but expecting a different outcome.

If I had gone through this series of events -- updated->mess & re-installed->updated->mess -- then I sure as heck wouldn't update the next time I re-installed until I figured out what the problem was.

If you keep doing the same thing then you won't be able to figure out what's wrong. If you figure out that it isn't a bad HDD or RAM, then start troubleshooting by applying one update at a time and testing the stability.

---

### Post by wieman01 on 2008-03-05
> **mozetti said:**
> Trying to inject a little humor here, but also serious:

They define "crazy" as doing the same thing repeatedly, but expecting a different outcome.

If I had gone through this series of events -- updated->mess & re-installed->updated->mess -- then I sure as heck wouldn't update the next time I re-installed until I figured out what the problem was.

If you keep doing the same thing then you won't be able to figure out what's wrong. If you figure out that it isn't a bad HDD or RAM, then start troubleshooting by applying one update at a time and testing the stability.
+1

Simple but valuable advice.

---

### Post by xdotx on 2008-03-05
memtest86+ followed by any appropriate HDD testing utils would be my plan.

---

### Post by kirsche on 2008-03-18
Went through the same last weekend - on a T60 too.
Tried GeUbuntu, XUbuntu and Ubuntu - for all 3 the same:

Install, apt-get update + apt-get upgrade = broken system.

Since I needed the system urgent, I took the easy route - re-format the root partition with ext3, basically don't use XFS !
I used Geubuntu again, install + upgrade -> all fine.

(Also have issues with xfs on another system, firefox crashing....)

---

