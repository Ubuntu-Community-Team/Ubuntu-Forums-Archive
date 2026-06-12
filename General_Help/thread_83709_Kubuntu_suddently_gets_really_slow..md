---
title: "Kubuntu suddently gets really slow."
date: 2005-10-29
forum: General Help
---

### Post by haaglin on 2005-10-29
Hi. I really need help with this. As the title says, my kubuntu becomes so slow, that i have to restart X to be able to do anything. This happens suddently, and i get no error dialog. It does not hang, but is unusable. my memory usage is at 100%. How can i locate the problem? 

My specs:
AMD Athlon XP2500+
1024mb DDR
Kubuntu Breezy
KDE 3.5 beta 1

I do have shadows on my windows, but not transparency. 
And this happens random, it doesn't happen when running the same program. 
also, i did not have this problem with Hoary.

---

### Post by katu on 2005-10-29
do you have a swap partition or a swapfile? I didn't and had a similar problem. 
If you don't, try here:
[http://www.ubuntuforums.org/showpost.php?p=287528&postcount=6](http://www.ubuntuforums.org/showpost.php?p=287528&postcount=6)

this doesn't make it permanent. to do that add the line:
/swapfile   none   swap   sw   0   0

to your /etc/fstab  . 

Hope this helps. if it doesn't help - give a description of what programs this happens with. (I had a problem with picture galleries for instance).
hope this helps,
Katu

---

### Post by blastus on 2005-10-30
Memory usage at 100% is normal. What does the "top" command in a Konsole show? You can also press CTRL-ESC to open up KDE System Guard and look at running processes to find out which one or ones are consuming the most CPU cycles.

---

