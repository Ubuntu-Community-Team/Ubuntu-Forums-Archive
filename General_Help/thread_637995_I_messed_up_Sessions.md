---
title: "I messed up Sessions"
date: 2007-12-11
forum: General Help
---

### Post by ultranoize on 2007-12-11
Hi I changed somethings in my session properties and now I don't have wireless, can't sudo can't iwconfig, ifconfig.  Is there a way of returning to a default configuration ??  I tried to look at the .gnome2/sessions file but it is kinda hard to read.

Thanks in advanced.

---

### Post by taurus on 2007-12-11
Maybe you changed your group ID?  What's the output of this command from a terminal?

```
id
```

---

### Post by ultranoize on 2007-12-11
This is the output... and the best thing is that i cant even start gedit....
```
uid=1000(santi) gid=1000(santi) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(santi)

```

---

### Post by taurus on 2007-12-11
What happens if you run gedit from a terminal?

```
gedit
```

---

### Post by ultranoize on 2007-12-11
nothing happens... but if afterwards i grep gedit:  ```
ps -ef | grep gedit
santi    24889     1  0 22:10 ?        00:00:00 gedit
santi    31985 31782  0 22:49 pts/6    00:00:00 grep gedit
 
```
so that means that the process is running but the window does not pop up.

---

### Post by ultranoize on 2007-12-11
Solved it... the hard way but it worked. I have another user (user2) in this same machine so I logged with user2 and under System > Preferences > Sessions  i clicked on "Remember currently running applications" in the tab called Session Options. By doing so, i get a file /home/user2/.gnome2/sessions which i used to overwrite  /home/user1/.gnome2/sessions. After a restart I logged on using user1 and everything is back  to normal.  Not nice, but it was effective.  Now the question still remains, can you somehow reload the default configuration for the session ??

thanks for your help.

---

