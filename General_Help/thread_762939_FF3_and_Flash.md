---
title: "FF3 and Flash"
date: 2008-04-22
forum: General Help
---

### Post by Het Irv on 2008-04-22
I upgraded to Hardy RC from Gutsy, got FireFox 3 and all that good stuff, but now sometimes my browser will just close when I try to view a flash video.  It's random and if I open it back up the video will work.

All the terminal will give me is segmentation fault.

---

### Post by sizzam on 2008-05-28
I was having the same problem with Flash videos crashing Firefox.  There is an open bug ticket for this here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)


I corrected the problem for myself with steps gleaned from the bug ticket, details are in this post:

[http://ubuntuforums.org/showpost.php?p=5057137&postcount=5](http://ubuntuforums.org/showpost.php?p=5057137&postcount=5)

I have been crash-free since performing these steps.

---

### Post by ubuntu-freak on 2008-05-28
Run this command:
 
**sudo apt-get purge flashplugin-nonfree libflashsupport**
 
Those with the 64-bit version of Ubuntu should also:
 
**sudo apt-get purge nspluginwrapper && sudo apt-get install nspluginwrapper**
 
Now skip to the manual install method for Flash in Part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683), then download and install v10 beta.
 
Nathan

---

