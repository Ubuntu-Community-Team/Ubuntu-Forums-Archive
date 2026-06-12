---
title: "New update breaks xorg"
date: 2006-08-21
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-08-21
The newest xorg update doesn't work. Now whenever I attemp to startx it can't find any screens. Everything was working fine before until now. I didn't install/remove anything or make any major changes to my system. What can I do to fix this problem ? Right now I am stuck at a console with the lynx webbrowser. Any help would be appreciated. Thanks.

---

### Post by meng on 2006-08-21
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
and then
startx
EDIT: fixed mistake

---

### Post by xXx 0wn3d xXx on 2006-08-21
> **meng said:**
> sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
and then
startx
EDIT: fixed mistake
Let me try and I'll see what happens.

---

### Post by bromleyi on 2006-08-21
Hi

Have same problem and have try the fix above. But it comes back as version not found.

Thanks
Ian

---

### Post by xXx 0wn3d xXx on 2006-08-21
Thank you ! I'm back at my desktop.

---

### Post by bromleyi on 2006-08-21
> **bromleyi said:**
> Hi

Have same problem and have try the fix above. But it comes back as version not found.

Thanks
Ian

Opps...I spelt it wrong.

All working now...

Thanks
Ian

---

### Post by ubuntu_demon on 2006-08-22
I've closed this thread. 

Let's keep this discussion in one place :
[B]
PLEASE READ: The Latest Updates Break the Xserver!
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)[/B]

---

