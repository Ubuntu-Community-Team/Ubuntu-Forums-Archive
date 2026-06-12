---
title: "&quot;Show Updates&quot; incorrectly empty 13.04 Xubuntu"
date: 2013-08-13
forum: General Help
---

### Post by bryguypgh on 2013-08-13
Using Xubuntu 13.04 x86-64, the last two days when there have been updates available and I've selected "show updates" from the notification icon, the list has been empty, but it reports (today) that 195k will be downloaded and the install now button is lit up. When I run apt-get upgrade it shows that there are in fact updates to install, today it's 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bamfdaemon libbamf3-1 libdvdnav4 lsb-base lsb-release
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 195 kB of archives.
After this operation, 16.4 kB of additional disk space will be used.
Do you want to continue [Y/n]

I did it from the command line yesterday and everything worked ok so it seems to just be a problem with the gui.Here's a screenshot of the update window:[ATTACH=CONFIG]245337[/ATTACH]

---

### Post by The Cog on 2013-08-13
I've got a screenshot just like that. In fact I've got two - one on my desktop, one on my laptop. So it's not just you.
I have no idea why the updates GUI list is empty though.

---

### Post by Dastardlydeed on 2013-08-13
Ditto. I've chosen not to update yet. Looks harmless though.

---

### Post by ibjsb4 on 2013-08-13
Synaptic, synaptic, synaptic :p

---

### Post by The Cog on 2013-08-14
Yes, actually I did run synaptic and "Mark all updates" just to check what was going on, and that the stuff was legit. I don't understand why the GUI update tool is blank though.

---

### Post by FearsomeGoat on 2013-08-14
Also have had this problem...is this just on Raring Ringtail? 
New to Xubuntu...it is beautiful...

---

### Post by The Cog on 2013-08-14
I hadn't ever seen that until a couple of days ago. Not on any other version, and not on Raring. 

Maybe a recent update to the utility introduced a bug. Maybe there is a certain category of updates that it doesn't show but I hadn't noticed before because there were always other updates listed as well.

---

