---
title: "samba client"
date: 2005-04-30
forum: General Help
---

### Post by elwis on 2005-04-30
Where does nautilius hide their samba config?

I have a terrible XP machine with a foldershare, Ubuntu mounts this one for me at bootup and puts a "shares" folder on my Desktop. Nice. 
However I can not add anythiong into it since it's owned by root, and I can't start any graphical apps as root (no xhost + won't work since GTK gives me an error message anyway)
so, mounting it in console without ro? Won't do, get error messages about bad fileystems, codepages and that aunt of mine.

So, my thought was. Somehwere there is acorrect smbmount string since that automount does it for me? But where the #¤&% is that one? it's not in /etc/fstab for sure..?

EDIT: Oh no, just noticed it's NTFS? could that be the problem, no mounting "rw" anyway??

---

