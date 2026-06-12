---
title: "Can't switch off"
date: 2008-05-19
forum: General Help
---

### Post by muteXe on 2008-05-19
Hiya,
Both my upper and lower panels on the desktop become "inactive".  By that I mean I go to to shutdown and click on the icon, and nothing happens.  I then noticed it wasn't just the shutdown icon, it was all of the top menu options (Apps, Places, System), and the lower panel as well.  It all looks fine and dandy, but clicking on anything in either of the panels does nothing.  I have to ctrl+alt+F1, then reboot from a command line.
This happens most of the time now, it isn't just a one-off.  Very annoying.
Any ideas?  
Many thanks,
mute

---

### Post by housam on 2008-05-19
right click and try to add new panel and add some icons on it and test it .it may work.

---

### Post by muteXe on 2008-05-19
Okay thanks, i'll try it when i'm back home tonight (at work now).
Cheers!

---

### Post by BillDozer on 2008-05-19
I experience the same behaviour. You just have to be patient, after some time (20 seconds up to some minutes) the shutdown dialog *will* appear.

It is very annoying and I hope someone has a solution to this. :mad:

---

### Post by Joeb454 on 2008-05-19
I think it may be a bug, you might want to check LaunchPad to see if there is anything on there. Alternatively, from a terminal you can always run ```
sudo shutdown -P now
``` to shutdown :)

---

### Post by prshah on 2008-05-19
> **BillDozer said:**
> I experience the same behaviour. You just have to be patient, after some time (20 seconds up to some minutes) the shutdown dialog *will* appear.

It is very annoying and I hope someone has a solution to this. :mad:

Take a look at post #2 on [http://ubuntuforums.org/showthread.php?p=4984991&highlight=gnome-power#post4984991](http://ubuntuforums.org/showthread.php?p=4984991&highlight=gnome-power#post4984991) for a quick and easy solution!

Note: This is _not_ related to the OP's problem. This is only for _your_ (BillDozer) problem.

---

### Post by muteXe on 2008-05-19
> **BillDozer said:**
> I experience the same behaviour. You just have to be patient, after some time (20 seconds up to some minutes) the shutdown dialog *will* appear.

It is very annoying and I hope someone has a solution to this. :mad:

I waited for over 20 MINUTES and the panel buttons were still not responding.

prshah:  Cheers mate, i'll give this a go tonight :)

---

### Post by prshah on 2008-05-19
> **muteXe said:**
>  By that I mean I go to to shutdown and click on the icon, and nothing happens.  I then noticed it wasn't just the shutdown icon, it was all of the top menu options (Apps, Places, System), 

> **BillDozer said:**
> I experience the same behaviour. You just have to be patient, after some time (20 seconds up to some minutes) the shutdown dialog *will* appear.

> **Joeb454 said:**
>  Alternatively, from a terminal you can always run ```
sudo shutdown -P now
``` to shutdown :)

It's not just shutdown; the entire panels have frozen.

Try killing and restarting the gnome panels: Open a terminal, then ```

sudo killall gnome-panel
``` that should automatically close your panels and then restart them.

If that doesn't work, switch to a virtual terminal with Ctrl+Alt+F1, then give the command ```
sudo /etc/init.d/gdm restart
```, then switch back with Ctrl+Alt+F7; are the panels working now?

---

### Post by muteXe on 2008-05-19
> **prshah said:**
> 

Try killing and restarting the gnome panels: Open a terminal, then ```

sudo killall gnome-panel
``` that should automatically close your panels and then restart them.



Hmm i can't open a termial (Alt+F2 has never worked for me), and the apps menu is of course still inaccessable.
Is:
```

sudo killall gnome-panel

```  
pointless to run in a virtual terminal?  If it is i'll just run 
```

sudo /etc/init.d/gdm restart

```  
i think.
But your first original suggestion means i probably won't have to do this.  Have I got that right?
cheers

---

### Post by vexorian on 2008-05-19
When this happens, I press ctrol+alt+backspace , it usually tells X.org to restart, but after pressing the shutdown button it will force it to close, and the shutdown process will begin.

---

### Post by prshah on 2008-05-19
> **muteXe said:**
> 
```

sudo killall gnome-panel

```  
pointless to run in a virtual terminal?  If it is i'll just run 
```

sudo /etc/init.d/gdm restart

```  


Virtual terminal is accessed by Ctrl+Alt+F1 to F4. Alt+F2 does not come into the picture. 

As a matter of interest, you can run the first command in Alt+F2 (By selecting the "Run in _t_erminal" option; not the second, since it will dump you to a command line interface rather than restarting the gdm. (However, you can recover by repeating the command with "start" instead of "restart")

Both commands are to do (essentially) the same thing; restart your panels. The first just kills and (auto-)restarts your panels, the second the entire gdm. Both can be run in a virtual terminal.

Both may or may not help. Actually, I will be a little surprised if it clears up the problem; I suspect a particular applet is causing the panels to freeze up. But we gotta walk before we run.

Post back if problems persist.

---

### Post by Joeb454 on 2008-05-19
> **prshah said:**
> Virtual terminal is accessed by Ctrl+Alt+F1 to F4. 

Actually I think they're a the true tty sessions. The terminal found under Applications > Accessories is a virtual terminal :)

[/offtopic]

---

### Post by prshah on 2008-05-19
> **Joeb454 said:**
> Actually I think they're a the true tty sessions. The terminal found under Applications > Accessories is a virtual terminal :)

[/offtopic]
 
What you say makes sense, and I thought so too; But everywhere I see, the F1-F10 terminals are reffered to as virtual terminals.

So... I apply the "when in Rome..." principle.

---

### Post by BillDozer on 2008-05-19
> **prshah said:**
> Take a look at post #2 on [http://ubuntuforums.org/showthread.php?p=4984991&highlight=gnome-power#post4984991](http://ubuntuforums.org/showthread.php?p=4984991&highlight=gnome-power#post4984991) for a quick and easy solution!

Note: This is _not_ related to the OP's problem. This is only for _your_ (BillDozer) problem.

Thanks prshah,

That was exactly what I needed!

---

### Post by muteXe on 2008-05-19
Seems like I have plenty to try tonight if it all goes pear-shaped again.
Many thanks again.

---

