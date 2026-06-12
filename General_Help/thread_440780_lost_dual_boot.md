---
title: "lost dual boot"
date: 2007-05-11
forum: General Help
---

### Post by Bashed on 2007-05-11
I installed XP to replace Vista partition today and I already had Ubuntu installed on a separate partition. However, now it does not dual boot but goes directly to XP. How can I reclaim the dual boot again?  The linux partition is still there.

---

### Post by m.musashi on 2007-05-11
Unless you deleted the partition with Ubuntu it isn't gone. The grub boot loader was just overwritten by windows. Pretty arrogant of windows too if you ask me. It's high time they respect that not everyone is a 100% windows users. Sorry, don't mean to rant. Anyway, you will need to use a live CD and boot from it. Open a terminal and type
```
sudo grub
```
You will get a grub prompt. Next type
```
find /boot/grub/stage1
```
It will say something like
```
grub> (hd0,3)
```
The 0 and 3 will depend on your setup. Next type
```
root (hd0,3)
setup (hd0)
```
with the 0 and 3 replaced by whatever is right for you setup. Then type quit and reboot. You should be good to go.

EDIT: more info [here](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) if you need it. However, I suggest you ignore the part about doing "setup (hd0,3)". It doesn't work in my experience. You want grub on the MBR so just use (hd0).

---

