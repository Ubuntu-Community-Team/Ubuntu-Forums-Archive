---
title: "Login as myself, I get only wallpaper and mouse. Guest acct works fine."
date: 2016-07-27
forum: General Help
---

### Post by brucew on 2016-07-27
I'm running a month old install of 14.04.5-LTS.

This morning when I went to work, I powered-down the system as normal and noted nothing amiss.  Nor was there anything remarkable during my session.

After work, when I login, I get my wallpaper and mouse pointer and nothing else.  Several retrys and after an fsck from the recovery menu, still yields the same result.  I've waited up to 15 minutes to be sure is wasn't doing something.  Just sits there, taunting me.

Yet, I can login using the guest account just fine.  That's where I am now.

I don't know where to begin troubleshooting, although I'm inclined to think that some key file in /home got written to a bad sector or somehow otherwise can't be read.

Fortunately, /home is on a separate drive, a month old Toshiba 4TB.  I have two copies of a recent rsync backup of it from Saturday.  I could nuke the whole thing, but I'd rather try first with a lighter touch.

Any suggestions?

---

### Post by GU4$+7rxH#@ on 2016-07-27
Hello

Press CTRL+ALT+F1, enter as root.

Enter those commands

> rm -r ~/.config  
rm -r ~/.compiz  
sudo restart lightdm 


---

### Post by CantankRus on 2016-07-27
Try resetting compiz first before removing whole config directories..... and is better to rename as .bak rather than removing when troubleshooting.
This will reset compiz/unity to defaults and reload.
```
dconf reset -f /org/compiz/ && setsid unity
```

---

