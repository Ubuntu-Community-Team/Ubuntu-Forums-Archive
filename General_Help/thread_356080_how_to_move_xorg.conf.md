---
title: "how to move xorg.conf?"
date: 2007-02-08
forum: General Help
---

### Post by sssp on 2007-02-08
I am new to linux and was trying to edit my xorg.conf file. I messed something up with my video card. Now it wont go into linux but I can still enter commands. I made a back up on my desktop of the xorg.conf called xorgbackup.conf. How do I move it to the correct folder to get back into linux??
I have tried:
"sudo mv root/Desktop/xorgbackup.conf etc/X11/xorg.conf"
It says:
"mv: cannot stat 'root/Desktop/xorgbackup.conf': No such file or directory"

Sorry if my question is confusing, i dunno how to explain it.

---

### Post by pay on 2007-02-08
```
sudo cp -r /home/<USER_NAME>/Desktop/xorg.conf /etc/X11/xorg.conf
```

---

### Post by meng on 2007-02-08
It could be /root/Desktop/xorgbackup.conf
or perhaps /home/**sssp**/Desktop/xorgbackup.conf
(substitute sssp with your username, btw)
but it won't be root/Desktop/xorgbackup.conf (note the / it's important!)

---

### Post by sssp on 2007-02-08
got it working, thanks for the quick replys.
I forgot the '/' in the beginning.
Thanks again

---

### Post by aysiu on 2007-02-08
If it's on *your* desktop, it wouldn't be in root. Try this command: ```
sudo mv ~/Desktop/xorgbackup.conf /etc/X11/xorg.conf
``` Otherwise, you can do ```
sudo dpkg-reconfigure xserver-xorg
``` to regenerate a new xorg.conf file.

---

### Post by sssp on 2007-02-08
it was in the root folder

---

### Post by aysiu on 2007-02-08
> **sssp said:**
> it was in the root folder
In that case, you were missing forward slashes. It should be ```
sudo mv /root/Desktop/xorgbackup.conf /etc/X11/xorg.conf
``` not ```
sudo mv root/Desktop/xorgbackup.conf etc/X11/xorg.conf
```

---

