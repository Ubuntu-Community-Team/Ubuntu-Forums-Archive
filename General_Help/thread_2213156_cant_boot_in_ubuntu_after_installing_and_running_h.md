---
title: "cant boot in ubuntu after installing and running hibernate"
date: 2014-03-25
forum: General Help
---

### Post by varun-10 on 2014-03-25
I have ubuntu gnome 13.10(dual boot with win7) and my home folder is encrypted
So I couldnt find a way to hibernate

What I did
```

sudo apt-get install hibernate
sudo hibernate
```

and now I am stuck at bootloader screen with last message like 
```
resume: libgcrypt version 1.5
```

Even the recovery mode is not working

Earlier when I ran into serious problems, I used to do a fresh ubuntu install, but this  time I have lamp server, hadoop etc set-up, and many important packages

If their is anyway to restore ubuntu or get my packages, and lamp server back, it would be very nice

---

### Post by varun-10 on 2014-03-25
I fixed it!
I am posting this solution in case anyone else is having the same problem

in grub, select ubuntu option and press e to edit

You will find a line at near end begining with word "linux"
 at end of line add word " noresume" (without quotes).

Boot in ubuntu by pressing control+z. Note grub does not save these changes permanently, and uninstalling this app( sudo apt-get remove hibernate) wont fix this.

To permanently fix, install grub-customizer and open ubuntu entry to make same changes and save it

---

