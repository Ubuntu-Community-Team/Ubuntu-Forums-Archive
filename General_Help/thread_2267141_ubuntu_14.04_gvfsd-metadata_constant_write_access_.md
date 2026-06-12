---
title: "ubuntu 14.04 gvfsd-metadata constant write access to drive"
date: 2015-02-27
forum: General Help
---

### Post by sp5 on 2015-02-27
Hello,
 

 Every day, randomly, gvfsd-metadata start writing to disk like there's no tomorrow.
 I first noticed this when I benchmark this drive and it wasn't a constant speed, so something else was using the drive. Using iotop gave me the answer, gvfsd-metadata was using the drive.
 

 This writing frenzy goes on for more that 15 minutes and I ended up killing the process.
 I'm on a ssd and while this write process was going on, writes speeds were at 14MB/s.  
 So you can imagine how much data is written at a speed of 14MB every second for over 15 minutes!
 It seems to be creating and deleting files, the same files just created.
 

 There's no high cpu usage just high, constant disk usage.
 I can't seem to duplicate the issue manually.
 I've already killed the process and deleted the content of the folder  ~/.local/share/gvfs-medata (in one instance and in another the folder itself) and it still comes back.
 

 Help.

---

### Post by pjpreilly on 2015-03-07
This can be easily recreated with the Super Start 7.3.3 extension in Firefox. Just right click on any tab to add to Super Start, click "Add this tab to Super Start" and the problem will occur in 12.04 as well as 14.04. In 14.04 the processor also saturates.

---

