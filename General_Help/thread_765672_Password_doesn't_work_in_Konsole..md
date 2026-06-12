---
title: "Password doesn't work in Konsole."
date: 2008-04-24
forum: General Help
---

### Post by Pepse3 on 2008-04-24
I was trying to install AVGFREE into my Kubuntu 7.04 and after installing the package I had to go to a Konsole to install the GUI and it asked for my password and when I put it in it came back with:  authentication failure  Sorry.  Now if it helps before I did this I re-booted the computer and I got a warning on the screen the says:  Starting wothout Administrative Priveleges!  You will not be able to apply any changes.  But you can still export the marked changes or create a download script for them.

  What happened?

Later. Pepse.

---

### Post by ibuclaw on 2008-04-24
Type into the terminal:
```
groups
```

And post the printed output

Regards
Iain

---

### Post by aysiu on 2008-04-24
What command did you use to install the GUI?

---

### Post by Pepse3 on 2008-04-24
jim@jims-computer:~$ groups
jim adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin


  Aysiu,  first to say I found some info through [http://ubuntu.com/community/Antivirus/Avg](http://ubuntu.com/community/Antivirus/Avg)  .  And in there I tried to follow the said commands but dbl clicking on the AVG folder on my dsktp didn't work so I right clicked on it and went to Kubuntu Package Menu and clicked install.  And it did.  So, then I went back and tried to use the commands from that using Option 1.  That didn't seem to be doing anything so I decided to reboot, and that's when I got the Admin priveleges warning and discovered I could log in as root.

Pepse.

---

