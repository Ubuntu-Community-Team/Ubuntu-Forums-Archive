---
title: "Restoring Linux bootability ofter WinXP installation"
date: 2006-11-02
forum: General Help
---

### Post by muxecoid on 2006-11-02
Hi. My WindowsXP worked well with GRUB dual boot, but WinXP died and I reinstalled it. During the installation it said, that it will temporarily make currently boot-able partition inactive and I can undo that via Control Panel->Administrative tools->Computer Management->Disk Management->Make active. **** Microsoft and Bill Gates personally, the "Mark Partition as Active" button is grayed. :( :( What needs to be done?

---

### Post by bulldog on 2006-11-02
Reinstall GRUB with the live cd.```
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 


[code]sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.
[/code]

---

### Post by muxecoid on 2006-11-03
Thanks, everything is working now.

---

