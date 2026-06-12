---
title: "Install wifi driver script"
date: 2008-01-24
forum: General Help
---

### Post by grogger13 on 2008-01-24
I have a problem with my wireless card where it has to be reinstalled every start up for some reason.  Im getting tired of having to do this ever time, then i realised i might be able to write a script.  I have never written any scripts before and only experience from c++ beginner programming in colllege, so i looked up a few things about writing scripts.

My idea was to create a script i could put in at start up that would go 1.remover existing driver installed, 2.installing driver again, 3 exit
Here is what i have so far.
```
#!/bin/sh
cd /wldrv
sudo ndiswrapper -r bcmwl5.inf
sudo ndiswrapper -i bcmwl5.inf
exit 0
```

I figured that if i wrote the script properly it should be a fine solution.  The problems that i have is with the sudo.  How can i get this script to just run in the background without be having to type the sudo password in.

---

### Post by bobyy on 2008-01-24
Hy maybe :first > $sudo chmod 777 script and now do the script executable> $sudo chmod +x script and after that just put the path to the script in /etc/rc.local  and it will start at boot

---

### Post by bobyy on 2008-01-24
Sorry ...for me is 5.00 AM .. :)) i see your point ...ignore my post..

---

