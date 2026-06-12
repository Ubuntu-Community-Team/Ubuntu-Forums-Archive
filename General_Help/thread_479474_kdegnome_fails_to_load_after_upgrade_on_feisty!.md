---
title: "kde/gnome fails to load after upgrade on feisty!"
date: 2007-06-20
forum: General Help
---

### Post by padmanabh on 2007-06-20
I put the PC on upgrade which was around 120 MB and went to sleep cause it was gonna take a while.

When I wake up, i found that it had gone into hibernate and was not responding to anything ...the screen was blank. 

So I restarted and now kdm refuses to load ...it says error in init..cannot find init image in "some mount point"

then it goes to text login prompt.

If i try to startx after  login...it fails to start...again some init error.

How do i resolve this? Is there any way i can go back to my previous configuration?

One more thing....the upgrade also upgraded my Nvidia graphics  drivers...is X crashing because of that?

Help.

---

### Post by kuja on 2007-06-20
That could be the cause of your x problems, try running "sudo apt-get update && sudo apt-get upgrade" again and see there are any problems or perhaps missed upgrades that it can grab.

---

### Post by padmanabh on 2007-06-20
I tried that...now here's the thing.

I ran "sudo apt-get update"....itsays some error in dpkg configuration run "dpkg --configure -a"
ran "sudo apt-get upgrade"....again same error message.

So i run "sudo dpkg --configure -a"....it says **error in file "/var/lib/dpkg/updates/0042" unexpected EOF encountered in the tag Description; Missing newline at end of file**

Now what do i do?

---

### Post by padmanabh on 2007-06-26
Someone...please help!!...

---

