---
title: "rebooted without nav bars"
date: 2008-05-29
forum: General Help
---

### Post by William.fries.is.here on 2008-05-29
i rebooted my comp this morning and now i font have any navigation bars anywhere  

how do i add them back? or just plain old fix this.

---

### Post by forestpixie on 2008-05-29
This might help you

[http://ubuntuforums.org/showpost.php?p=4663517&postcount=9](http://ubuntuforums.org/showpost.php?p=4663517&postcount=9)

---

### Post by William.fries.is.here on 2008-05-29
the question is how does one access the terminal without the panels

---

### Post by William.fries.is.here on 2008-05-29
> ill@will-desktop:~$  gconftool-2 --shutdown rm -rf ~/.gconf/apps/panel pkill gnome-panel
Error while parsing options: Unknown option -rf.
Run 'gconftool-2 --help' to see a full list of available command line options.
will@will-desktop:~$ gconftool-2
Run 'gconftool-2 --help' to see a full list of available command line options.
will@will-desktop:~$ gconftool-2 rm -rf ~/.gconf/apps/panel pkill gnome-panel
Error while parsing options: Unknown option -rf.
Run 'gconftool-2 --help' to see a full list of available command line options.
will@will-desktop:~$ rm -rf ~/.gconf/apps/panel pkill gnome-pan

doesn't look like i have had any luck

---

### Post by forestpixie on 2008-05-29
You can get a terminal - Alt+F2, put gnome-terminal in command to run

There are 3 seperate commands to run in that post

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by William.fries.is.here on 2008-05-29
> will@will-desktop:~$ gconftool-2 --shutdown
will@will-desktop:~$ rm -rf ~/.gconf/apps/panel
will@will-desktop:~$ pkill gnome-panel
will@will-desktop:~$ 

doesn't seem to have any effect should i reboot?

---

