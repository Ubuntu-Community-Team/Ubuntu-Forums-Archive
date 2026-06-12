---
title: "Can't load boot screen"
date: 2007-06-22
forum: General Help
---

### Post by leejames07 on 2007-06-22
Ok This could seem bad.

Well i loaded up my computer and got round to loading the boot screen but wouldn't :( if i remember it was the error GRUB 1.5  then error 22. I thought i could reinstall Ubuntu from the live CD so i try that and it say it can't execute hda01 (I think the one at 94%) then stops. So i try and get the windows boot screen through recovery mode but i have the problem where it doesn't recognise the new administators password and i don't want to call Microsoft at high rates so i would to fix it myself. Would running the boot CD and in the terminal but either
```
fsck hdb1
```

or```
fsck -f hdb1
```

Please help

---

### Post by alienexplorers on 2007-06-22
Are you dual booting.  If so put your windows disk in and boot to recovery mode.  Enter:
> fixmbr
If you are not dual booting insert your live-cd and boot it.  Go into terminal and enter sudo grub.
Enter:
> find /boot/grub/stage1
You will get an output such as (hd#,#).
Enter:
> root (hd#,#)
Enter:
> setup (hd#)
exit grub editor
reboot

---

### Post by leejames07 on 2007-06-22
Like I said i cannot get into recovery mode as it doesn't recognise my password so could i still do the live cd one even if i am dual booting

---

### Post by leejames07 on 2007-06-22
Sorry for the double post but does anyone know how to access my documents on my hard drive with another computer as a slave as i want to back up some files is there a way to do this

---

