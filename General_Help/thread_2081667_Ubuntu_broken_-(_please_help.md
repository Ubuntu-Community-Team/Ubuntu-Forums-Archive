---
title: "Ubuntu broken :-( please help"
date: 2012-11-07
forum: General Help
---

### Post by tony.morse on 2012-11-07
Hi,

So I had a working system with 11.10 and wanted to make some changes so before doing this I thought I should back up the existing system so I can go back if I mess things up. I used Clonezilla in basic mode to clone from the system disc to an identical disc in the same machine, and Clonezilla seemed to think everything went fine. However now I can't boot from either disc?

My first step was to reinstall grub using boot repair
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```

Now the grub loader appears to work but when I select an ubuntu to boot it goes to a blank screen and stays there forever.

I can however ssh into the machine from another computer though the terminal is incredibly slow ?

If I select the recovery mode from grub I get the screen with the options menu on it but then a load of text covers this up with text about USB?

I can boot from a live disc and then fun fsck which works fine and finds no problems.

I've reached the limit of my knowhow and I'm not sure what to try next? maybe it could be a graphics problem? something in Xconfig? err... how to check and what to look for???

All your help much appreciated, I need to recover this system and not simply re-install from scratch...

---

### Post by tony.morse on 2012-11-07
UPDATE:

Ok just re-started the machine and as if by magic it worked!!! it booted fine.
So I swapped HD's and the other HD didn't boot, so I swapped back and now the first one doesn't boot either???

(I only connect one HD at a time using the same SATA cable)

?????

---

