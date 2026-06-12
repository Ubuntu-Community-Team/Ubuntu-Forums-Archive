---
title: "Ipod wont even show as /dev/&lt;xxx&gt;"
date: 2013-12-29
forum: General Help
---

### Post by Tristan_Williams on 2013-12-29
I am running Ubuntu 13.10 Minimal, with xfce4 installed.
I have libgpod, libimobiledevice4, and other ipod related packages installed.

I have an Ipod 4th Generation, with iOS 6.1.5

I plug in my ipod an absolutely nothing happens. The ipod will charge, but thats it...

It won't even show up as a /dev/<xxx>, so I cant manually mount it.

How can I get it to where I can mount it?

---

### Post by J_Me on 2013-12-30
'cat /proc/partitions' will list your media even if it's not mounted. Which type of ipod do you have. cheers

---

### Post by Tristan_Williams on 2013-12-30
Ipod touch 4g with iOS 6.1.5

---

### Post by J_Me on 2014-01-01
From my experience the 2nd generation ipod touch with the original firmware used to work(sync) with amarok but once I upgraded the firmware to IOS4.x.x it stopped syncing, I can now only read the mp3's but not upload anything so now I use itunes. Maybe things have changed recently, try 'ifuse' create a folder on your desktop then run 'ifuse /home/me/theFolder' and see if it mounts. Did 'cat /proc/partitions' list your ipod's path.

---

