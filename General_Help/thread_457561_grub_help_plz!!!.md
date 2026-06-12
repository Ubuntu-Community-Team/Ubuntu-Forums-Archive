---
title: "grub help plz!!!"
date: 2007-05-28
forum: General Help
---

### Post by carlitx on 2007-05-28
yes im kind of new to ubuntu and im using the latest version. but thats besides the point, i have installed the grub boot menue and was always able to selct my windows xp os for gaming and doing school assignments on XP. but one day when i restarted to switch from ubuntu to XP when grub loaded up no windows selection. and when i let it time out to see if it wne with my default settings to auto load windows after 30 seconds, it loaded ubuntu. :@:@. ive tryed doing the reinstalling commands in terminal, still no go...so what do i do??? it worked fine before....plz respond asap plzzz.....

---

### Post by strabes on 2007-05-28
Just add a windows option to the end of your /boot/grub/menu.lst:

```
sudo gedit /boot/grub/menu.lst
```

> title		Windows XP Pro LOL!!!!!!!!!
root		(hd0,0)
savedefault
makeactive
chainloader	+1

This example (copied directly from my menu.lst) assumes that windows is on the first partition of your first hard drive. If you want windows to be the default boot option, simply paste it above the other boot options in menu.lst. Be careful to not mess up this file because at your level it would take some work to fix it.

---

### Post by HW_Hack on 2007-05-28
If you are unable to get Grub edited and XP booting - you may have to use drastic measures --- meaning repairing your Master Boot Record --- this will end up blowing Grub away (from your boot sector) but XP will now boot 


[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)


Good luck --- your Linux partition will still be there but you'll need to re-create grub etc

---

