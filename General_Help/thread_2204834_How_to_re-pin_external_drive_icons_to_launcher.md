---
title: "How to re-pin external drive icons to launcher?"
date: 2014-02-10
forum: General Help
---

### Post by Roasted on 2014-02-10
Hello friends. Just curious, let's say I have another partition on my drive. By default an icon sits in the panel. Let's say I removed it but later want to re-add it. How can I do so?

Thanks!

---

### Post by varunendra on 2014-02-13
Usually the icon of a partition shows up in the launcher only when it is mounted at /media/<some mount-point>. It is automatically removed from there as soon as it is unmounted.

So.. do you mean it was showing up in the launcher (I mean Unity launcher in the left) permanently? Accordingly, did it use to be mounted permanently?
If yes, that can be done by adding it to the /etc/fstab file, mounting it at some mount-point in /media.

---

### Post by Roasted on 2014-02-13
No - it was not mounted. I have 3 partitions on this hard drive.

15GB for root
200GB for home
15GB for testing another distro on physical hardware

The last partition was showing up on the Unity bar. It was not mounted. I removed it, and got to thinking - how can I re-enable that if I so choose?

It's more curiosity than anything else. :D

---

### Post by deadflowr on 2014-02-13
I know you can set it with Myunity in 12.04 to always, never and the default, show when mounted.
You can also set this in ccsm > unity plugin> experimental.

How to set it in newer version probably differs, since MyUnity doesn't exist for newer releases.
I'm sure the setting is still in ccsm, though, and there is probably an easy to set gsettings command for it.

---

