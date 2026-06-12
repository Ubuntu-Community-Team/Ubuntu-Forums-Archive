---
title: "HELP! I accidentaly moved many folders from root directories!"
date: 2017-11-16
forum: General Help
---

### Post by di-mk1 on 2017-11-16
So, I was in a folder where I maintain many other folders and subfolders. I accidentally run the command:

```
find /*/* -prune -type d -exec mv -t /home/myname/Music/Jazz/test {} +
```
obviously without knowing what I was doing. Now I see hundreds of folders coming from root directories in the target directory. I assume I moved folders from **/lib**, **/proc** and others. I'm afraid to restart the pc. Is there any way to reverse what I did?

---

### Post by Impavidus on 2017-11-16
Ouch...

If you ran that command while you were not running a root shell, nothing shoud have happened. That's why you shouldn't run root shells unless you really need them.

This moved all subdirectories of /etc, /boot, /var etc. They should be fairly conspicuous in your /home/myname/Music/Jazz/test/ as they will be (mostly) owned by root, and you can use find to search for those root-owned directories, but there's no automatic way to find out in which directory they belong. I mean, /home/myname/Music/Jazz/test/grub/ must be moved back into /boot/ and /home/myname/Music/Jazz/test/grub.d/ must be moved back into /etc/ and there no automated way to do that. And I somehow doubt your system will still work reliably now that you moved /usr/lib, /usr/bin and /lib/x86_64-linux-gnu.

You could try a live disk and move the directories back to where they came from, one by one, and on my system that would be 454 directories, but you have to guess somehow where they came from. Actually, a bit less, as you don't have to bother about /proc, /tmp and /sys as those are recreated on reboot.

However, I think reinstalling may be easier.

---

### Post by di-mk1 on 2017-11-17
Thankfully I was not sudo. I prepared for a full restore and went on deleting the moved files and restarted the pc. All well, breathing calmly now. Thanks for the prompt response though.

---

