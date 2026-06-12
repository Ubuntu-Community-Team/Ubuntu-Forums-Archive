---
title: "Possible to restore sudoers file w/o CD?"
date: 2007-09-09
forum: General Help
---

### Post by climbjm on 2007-09-09
I made a back up copy of my sudoers file.
I messed up my sudoers file and cannot "sudo" anything now.
I dont know my "root"s password.

Anyone know of any tricks to restore it to my back up not using:
 * The Live CD
 * Using user root
 * Using "sudo" cp

---

### Post by p_quarles on 2007-09-10
There are two reasons I can think of not to use the live CD to fix this:
1) Your CD drive is broken

If this is the problem, you should check if your BIOS supports either USB or network booting. If so, you'll be able to either A) load the .ISO onto a USB thumb drive and boot from that; or B) (if you have another computer) boot into an installation image over the network.

2) Your internet connection is slow, and you lost your installation CD. 

In this case, you should either suck it up and re-download the file, or order a (free) CD from Canonical. Whichever is more reasonable.

---

### Post by McNils on 2007-09-10
Restart your computer in recovery mode. You get logged in as root. Just copy the original file back with cp. And finally restart.

Be very carefull when editing the sudoers file. Always use **visudo**. Me thinks that you can use your favorite editor with the VISUAL environment variable set.

---

### Post by climbjm on 2007-09-10
So when I ran visudo to edit my sudoers file the first time... it opened it in nano.  Does that sound right?

---

### Post by McNils on 2007-09-11
Yes, that could be correct it depends on your environment. The environment variables VISUAL and (fallback) EDITOR controls wich editor is started.

---

