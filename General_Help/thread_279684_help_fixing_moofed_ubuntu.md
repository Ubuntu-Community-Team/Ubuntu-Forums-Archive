---
title: "help fixing moofed ubuntu"
date: 2006-10-18
forum: General Help
---

### Post by leahcimic on 2006-10-18
I hope someone can help me. I've been using ubuntu for a long time now. I just installed windows on a seperate partition. I was aware of the fact that windows would replace my boot loader so i re-installed it. Everything was fine. Once while windows was loading it decided to check my filesystems, it came accross the linux partition and started "FIXING" it. It's reiserfs, I have no idea why windows would touch this but I saw it trying to update 'file indexes' and quickly shut it off. Linux now does not boot. I have /home on a seperate partition and I have not lost anything here. However I've been mucking around with the live cd and chrooting me into the affected partition. Most things seem to work fine, I was wandering is there a way I can search for corrupt packages and replace them? I thought a sudo apt-get remove ubuntu-minimal and then re-install it would fix my issues but i hasn't. When I removed the ubuntu-minimal it seemed to only remove the meta-package and not the packages it depends on... is there a way i can remove everything from the ubuntu-minimal meta package ? I look forward to anyones help. Also I've tried chrooting and setting my DISPLAY variable to :0.0 and running synaptic but it does not connect... I am probably going the wrong way about it, but I'm sure it's possible some how... Any ideas ?

---

### Post by Malakia on 2006-10-18
Try sudo aptitude remove instead of apt-get that should remove all the dependecies associated with it. Then when you reinstall use aptitude instead of apt-get.

---

