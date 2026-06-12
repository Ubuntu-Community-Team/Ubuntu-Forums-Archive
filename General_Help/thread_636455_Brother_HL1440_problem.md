---
title: "Brother HL1440 problem"
date: 2007-12-09
forum: General Help
---

### Post by chrisyuan01 on 2007-12-09
Hey everyone, I am having trouble with my brother HL1440 printer driver on my new Ubuntu system.  I have gotten the LPR driver all downloaded, and when I try to install it, it doesnt work.  I try installing it again, and it spits this at me:
E: The package hl1440lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
Can anyone tell me whats wrong!  Thanks, because I cannot install any packages while this problem is going on, and I need to install much more!

---

### Post by gajohnny on 2007-12-31
I had this same problem. 

I had to create an empty file at /etc/init.d/lpd.  

To do this I went to the terminal and typed 

gksudo nautilus

which allowed me to create the folder in the /etc/inti.d/ folder

After that I  followed  the instructions from the Brother site to the letter ([http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html))

Then I followed the instructions on the brother site especially the part about creating  a symbolic link between the lpd file and the cups file (this may also be a cupsys file, you will need to look in the /etc/init.d/ folder to see if you have cups or cupsys).  I am not sure how this worked but it cleared the error from synaptic and I am able to add and remove packages without errors.

I hope this helps

---

