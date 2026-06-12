---
title: "System going slow then freezing then giving slow moving then freezing again"
date: 2007-12-27
forum: General Help
---

### Post by sefs on 2007-12-27
Hi there all,

My sytem is grinding to a halt and freezing forcing me to do a hard reboot.  sometimes the mouse can be moved but it moves really slow then freezes again but get no response from system.

How do I go about tracking this problem down.

Thanks.

EDIT:  It seems that when this happen only the mouse works intermittenly and it has the busy cursor icon but its not animated, its stuck but still the mouse can be moved.  But everything else is frozen and non responsive.

---

### Post by Bungtung on 2007-12-28
These symptoms might indicate a missing or non-functioning swap partition (as the system runs out of ram it slows and then locks).

To check this navigate through the menu to System/Administration/System Monitor and look at the Memory and Swap History section.  Is the swap partition showing signs of activity?

---

### Post by sefs on 2007-12-28
I've attached a png of the history is there anything specific i should look for in it? 

Aslo with 2GB of mem I have the swap set to 2GB should it be bigger? smaller?

How can I ensure that the swap is functioning properly.

I've also attached some other pngs, one of gparted which shows the swap, fstab, which shows the mounting of the swap, and on on the conkey dispay which somehow is not picking up the sway...Not too sure why that is.

---

### Post by sefs on 2007-12-29
I think my swap was indeed non-functional somehow, so i set it back, will see if the freezing still occurs, thanks for your help.

---

