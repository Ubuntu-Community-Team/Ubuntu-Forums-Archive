---
title: "restore /etc/ permissions"
date: 2013-12-13
forum: General Help
---

### Post by pseudocp on 2013-12-13
Hey guys,

Im forced to use Ubuntu for some time now (LTS 12.04) and finally did my long overdue 'kill ubuntu in one hit' mistake. Please dont tell me how dumb it was, Im feeling already bad enough at the moment..

I wanted to debug some issues with extern hardware and set temporarily the permissions of /etc/ and a subfolder of it to 777. However when I wanted to undo this, I misstyped the permissions of /etc/ to 766 instead of 755, that means I have no more control over linux (esp. sudo etc).
Is there any way to restore the rights of /etc/? Can I do it with an extern knoppix live (or similar) cd?
Or do I have to save the data and reinstall?

Thanks in advance!

---

### Post by steeldriver on 2013-12-13
Hello and welcome to the forum

Provided you didn't add the recursive flag (-R) to the chmod command, then it should be simple to fix - although if the current permissions have broken sudo you will need to do so either by booting into recovery mode or from a live disk / USB

If you do it via recovery mode you will need to remount the filesystem with write permissions first

```
mount -o remount,rw /
```

If you use a live disk, it should just be a matter of creating a suitable mount point, identifying the HDD's block device, and mounting it (still a few more steps than using recovery mode though)

---

### Post by pseudocp on 2013-12-13
If I try to use the recovery mode (I think you mean the 'Drop to root shell' option?), it says that it wants the root password. Afaik there is no root password set, other then the one I use for sudo. 
> **steeldriver said:**
> If you use a live disk, it should just be a  matter of creating a suitable mount point, identifying the HDD's block  device, and mounting it (still a few more steps than using recovery mode  though)
Do you know a fine step by step tutorial for that?

---

### Post by Impavidus on 2013-12-13
It shouldn't ask for a root password in recovery mode (indeed, in the grub menu "recovery mode", then "drop to root shell"), unless (maybe) when you use sudo. There's no need for sudo in the recovery console, as you are already root.

---

### Post by pseudocp on 2013-12-13
> **Impavidus said:**
> It shouldn't ask for a root password in recovery mode (indeed, in the grub menu "recovery mode", then "drop to root shell"), unless (maybe) when you use sudo. There's no need for sudo in the recovery console, as you are already root.

Thats really weird, the prompt says "give root password for maintenance or press ctrl+d to continue". Typing my password or just pressing enter doesnt bypass this.

---

### Post by mattholl82 on 2013-12-13
Try to select "enable networking" before going to the root shell.  That should mount everything with read and write access....

---

