---
title: "Read only filesystem!"
date: 2005-06-09
forum: General Help
---

### Post by basementjack on 2005-06-09
Hi everybody..

I don't know what is wrong.. But it started right after an atempt to download a couple of Mythbusters-clips with Gnome Bittorrent.. I cannot use any thing on my harddrive.. I cannot create a new file on my Desktop.. If I try to open Home folder in Places it says IO Error Read only filesystem...

Why is my hd suddenly read only?.. and how to fix it?..

Thanks in advance, 
basementjack

---

### Post by basementjack on 2005-06-09
Well.. I rebooted and it stopped in text-mode!.. But it provied me with the answer.. 

```

mount -n -o remount,rw /
fsck -y
reboot

```

I think that how I did it.. Took me some time..  :razz:

---

