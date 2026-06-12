---
title: "Keyboard doesn't work in X"
date: 2006-12-14
forum: General Help
---

### Post by maniacmusician on 2006-12-14
Okay, having the weirdest problem. my keyboard stops working after I log into an X session. At first I thought it might just be because of beryl, but I disabled that and the problem is stil there. So, I'm stumped. I don't want to reconfigure my xorg.conf because I just got it set up perfectly a couple of days ago. I guess if worst comes to worst I will back up my current xorg and do a reconfigure. right now, i'm writing this from Links, the command line browser. 

Before you ask, I've already tried the following:
Restarting X,
Restarting computer,
unplugging and plugging in keyboard
trying a different keyboard

and none of these have worked. Thansk for reading, I hope there's an easy fix for this.

-MM

---

### Post by maniacmusician on 2006-12-14
okay, so bad news. I just did a dpkg-reconfigure xserver-xorg and that still didn't fix it! I have an intense amount of work to get through and desperately need my keyboard so any help would be awesome.

If a reconfigure didn't fix it, what could it be? and it was a very sudden thing too, it just stopped working...

---

### Post by maniacmusician on 2006-12-14
This is f*cking weird; it's working again. I don't know what's wrong with this installation, it's been acting up a lot lately.

Thanks anyways...

---

### Post by mindspin on 2006-12-15
Hi, I fixed it with configuring xorg.conf like mentioned in [http://www.ubuntuforums.org/showthread.php?t=317424&highlight=keyboard]("http://www.ubuntuforums.org/showthread.php?t=317424&highlight=keyboard")

disabling acpi (as mentioned in the above thread did not help at all)

good luck

---

### Post by maniacmusician on 2006-12-15
thanks but as my posts after the first one say, the problem fixed itself for some reason. Really weird.

---

