---
title: "How to avoid or debug occasional kernel panics"
date: 2017-11-19
forum: General Help
---

### Post by danizen on 2017-11-19
I have a Dell Lattitude E6410 laptop, which has been running flawlessly with Ubuntu for quite awhile.   When I updated from 16.04 LTS to 16.10 (and thence to 17.04), the screen started occasionally going mostly blank and showing a couple of vertical and horizontal lines.   For awhile, I assumed that it was a video driver problem, but I have since done the following:

 * Done a backup of critical files (Documents, Music, and Pictures)
 * Upgrade the BIOS 
 * Done a safe-mode memory test
 * Attempt to ssh into the system after it happens (Openssh-server was not installed, so no luck, now it is installed)
 * Disabled a bunch of services I don't need all the time, such as apache2, mysql, postgresql
 * Removed a bunch of packages I don't need at all, like libvirt, etc. - I now use VirtualBox and vagrant or Docker, exclusively.

Since I haven't eliminated video driver problems, which logs would I look into to determine whether there were video driver problems?
Should I change my display settings to something "safer" to avoid the problem, and see with what it is correlated?

What should I think of that I haven't thought of?

---

### Post by dragonfly41 on 2017-11-20
For me, trying to understand log files to pick up clues is a nightmare.

I created a workflow to apply semantic analysis to system logs.

This is based on using tools such as TextSTAT to run concordance analysis and then 
look through the word forms to locate clues which you follow up in google search.

I explained the workflow I use in this thread ... post #8
[URL="http://https://ubuntuforums.org/showthread.php?t=2370564&highlight=TextSTAT"]
https://ubuntuforums.org/showthread.php?t=2370564&highlight=TextSTAT[/URL]

Since recently purchasing a Dell 3268 tower PC my freezes have gone.

---

