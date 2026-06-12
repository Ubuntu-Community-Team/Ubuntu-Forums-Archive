---
title: "Can't login into my account,,"
date: 2015-12-01
forum: General Help
---

### Post by rudwan2 on 2015-12-01
This happened to me before but fixed it  .I think it was something to do with Xauthority file, well that time I could at least log in as root from crtl +alt + F1.Now I can not log in as root from the root terminal also can't even get Into guest profile, the same black page quickly flashes than am back at the log in screen. The only area I can enter is grub minimal bash command line. What is problem and how do I fix this.Thanks.

---

### Post by QDR06VV9 on 2015-12-01
Was the fix you used something to this effect?
```
[COLOR=#111111][FONT=Consolas]sudo mv ~/.Xauthority ~/.Xauthority.backup
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo service lightdm restart[/FONT][/COLOR]
```

If not tell us what DE you are using IE Ubutnu, Gnome, XFCE, Mate.
Regards

---

### Post by rudwan2 on 2015-12-01
I have Ubuntu 14.04 LTS.
I fixed it last time with. 
mv ~/.config/xfce4{,.bak}

---

### Post by QDR06VV9 on 2015-12-01
Post back the output of this in the terminal
```
[COLOR=#111111][FONT=Consolas]echo $DESKTOP_SESSION[/FONT][/COLOR]
```

---

### Post by rudwan2 on 2015-12-02
I can't get into any terminal including.recovery root terminal ,as it says login incorrect when I type my password. I can only enter grub minimal bash command line

---

### Post by rudwan2 on 2015-12-02
Any help?

---

### Post by QDR06VV9 on 2015-12-02
I'm not sure how to help if you can not get to a terminal!

---

### Post by QDR06VV9 on 2015-12-02
Something just came to me. If you have your install CD or USB
In the LiveCD, Try Ubuntu without installing and pull up the terminal and enter 
```
gksu nautilus
```
Browse to your home Directory, And also show hidden files needs to be enabled, then find the .Xauthority file and either delete it or move it to another directory like Documents or your choice.
And Also you had mentioned that you had a xfce4 fix at one time also, So go ahead and move that file to the same folder that you put the .Xauthority in.
That file should be in <.config/xfce4>
Then see if you can now reboot and login.
**No guarantee so make sure you have a good backup system in place**..
Good Luck and Fingers Crossed

---

