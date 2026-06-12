---
title: "Entered sudo code that didn't work from a forum. Did I damage my computer?"
date: 2019-01-04
forum: General Help
---

### Post by scribner on 2019-01-04
So I made the mistake of blindly entering sudo code from a forum, which didn't work. I was trying to add exFAT to my system, so my computer could read my camera's memory card. This was the code I entered: 

> OK from what I read at the ubuntu site you open a terminal and enter  again without quotes "sudo add-apt-repository ppa:relan/exfat" then  enter "sudo apt-get update && sudo apt-get install fuse-exfat  exfat-utils"

That code doesn't work.

I later ended up following the instructions for one line of code at [https://itsfoss.com/mount-exfat/](https://itsfoss.com/mount-exfat/) -- which did work.

I was wondering what code this guy had me enter and if there's any chance I damaged or corrupted my computer.

---

### Post by deadflowr on 2019-01-04
A dated command.
It seems the relan/exfat ppa no longer exists.

You should clear the system of the added repository information you tried to add.
Simply re-run the command but with an -r option, which will remove the added entry.
```
sudo add-apt-repository -r ppa:relan/exfat
sudo apt update
```

Once you clear out the broken ppa entry the system should be fine.

---

### Post by scribner on 2019-01-04
> **deadflowr said:**
> A dated command.
It seems the relan/exfat ppa no longer exists.

You should clear the system of the added repository information you tried to add.
Simply re-run the command but with an -r option, which will remove the added entry.
```
sudo add-apt-repository -r ppa:relan/exfat
sudo apt update
```

Once you clear out the broken ppa entry the system should be fine.

You're awesome! Thanks!

---

