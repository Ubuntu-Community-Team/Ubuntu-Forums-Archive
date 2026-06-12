---
title: "Azuerus Downloading error"
date: 2005-06-19
forum: General Help
---

### Post by TristanMike on 2005-06-19
So I have a 80 GB 3 Partition Drive (XP, FAT32, Ubuntu).  I've made my /windows directory able to read/write after a long day and lots of help from this community.  The intention, mainly, was to make /windows available for torrent downloads both accesable in XP and Ubuntu so that no matter what OS I'm under, I can continue downloading the file.  I can now save files via Firefox to the /windows directory, I can move files into it as well.  However, when I open a torrent file and save it to /windows, I get this error under the "Status" tab.....

Error: Operation not permitted, setLength fails (allocateFiles new:/windows/the Dark Crystal DVD rip.avi)

I can see peers in the swarm, but the error is in red.  Can I do this in Linux, or does the file HAVE to be saved to the local drive then moved once completed.

It works fine when saving locally, just not to /windows, not a massive issue, just one for my personal comp. tweaks and any help would be appreciated.

Be aware I am a COMPLETE noob to not only Linux, but to computers in general.

Thank You
TristanMike

---

### Post by blind0wl on 2005-06-20
Well I assuming that your windows folder will get mounted with root permissions.  And then Im assuming Azuerus runs as your local user.  Youd have trouble writing to your windows partition without Azuerus ran as root....give it a go as root.

---

### Post by TristanMike on 2005-06-20
Yeah, that seems feasable, now, would someone please let me know how I'm to run a program as root?  I'm still on a MASSIVE learning curve.....

Thank You
TristanMike

---

### Post by blind0wl on 2005-06-20
Im not sure what the executive program from azeurus would be, but id try

```
sudo azeurus
```

From a terminal window.

Good luck

Blindy

---

