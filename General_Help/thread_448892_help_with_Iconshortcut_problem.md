---
title: "help with Icon/shortcut problem"
date: 2007-05-19
forum: General Help
---

### Post by Drawde on 2007-05-19
Hello, I've searched the forums and have not been able to find anything similar to my problem.

Just recently most of the icons on my system stopped showing.  It is really hard to explain, so here is a screenshot of what I'm talking about:

[[IMG]http://img383.imageshack.us/img383/2590/noiconseb2.th.png[/IMG]](http://img383.imageshack.us/my.php?image=noiconseb2.png)

Desktop icons now have a visible ".desktop" extension and nautilus is showing ".drive" after most of my drives.  I assume it is a problem with nautilus, but I haven't been able to find out what is causing it.  The links no longer work as a link now.  Has anyone ever seen anything like this?

---

### Post by Psicolonia on 2007-05-19
try:

sudo chmor a+wr -R /tmp

and reeboot

---

### Post by Drawde on 2007-05-19
I tried "sudo chmod a+wr -R /tmp" but that didn't solve the problem.  
The last thing I remember doing before the problem occurred was looking at some of the desklets for gdesklets (which was installed and running prior to this problem).  Its almost like whatever was responsible for making the system icons just stopped working.  Thanks for your help so far though!

---

### Post by Drawde on 2007-05-20
I have renamed my ".thumbnails" folder to see if a new one would be generated, but the folder is never recreated after rebooting.  Does anyone know what handles thumbnails in ubuntu?

---

