---
title: "What is wrong with my keyboard"
date: 2008-04-09
forum: General Help
---

### Post by ramkumail on 2008-04-09
Hi,
 After upgrading to hardy and installing gnome-do, i found a weird thing. The hot combination super+space works only if i use th super key to my right. if i press left super key immediately a message pops up saying 

"No terminal command has been defined".

My keyboard is exactly same as the one here.
[http://www.seoconsultants.com/windows/keyboard/](http://www.seoconsultants.com/windows/keyboard/)

In the gconf editor where shortcuts are defined, it is
[[IMG]http://img241.imageshack.us/img241/5835/screenshotconfigurationzt1.th.png[/IMG]](http://img241.imageshack.us/my.php?image=screenshotconfigurationzt1.png)

Please help me out. I suspect the problem is in choosing the right keyboard lay out. I tried choosing microsoft natural from layout but that didn't solve the problem. Thanks in advance.

---

### Post by fguilhon on 2008-04-10
I don't think it is a keyboard prob.
It is more likely a shortcut conflict with compiz.
Compiz includes new shortcuts using the Super key. You can look for them in compizconfig-settings-manager app.
Good luck and let us know your results.

---

### Post by ramkumail on 2008-04-11
Thanks for the reply. The problem comes only when metacity is running. if compiz is switched on both the super keys work nicely. I as well checked my compiz config settings shortcuts. i didnot find any conflict. what else can i try to correct the problem?

---

### Post by fguilhon on 2008-04-14
you can try looking up on gconf-editor in apps/metacity for keybindings...

---

### Post by ramkumail on 2008-04-18
sorry for double post

---

### Post by ramkumail on 2008-04-18
I have checked that. nothingseems to be wrong. let me state the problem again for clarity.

only one of my super keys doesnt work(the one to the left side of space bar). the other one (one to the right of space bar) works perfectly fine while running metacity. while running compiz both keys work nicely. What can possibly be the reason? it has been two weeks and i cant figure out what is wrong. must be the perfect noob on earth. Anyway has any one got any clue why this is happening?l linux gurus,are you guys out there? :confused:

---

### Post by bingoUV on 2008-04-18
Can you post the output of the following command : 
```

xmodmap

```

---

### Post by ramkumail on 2008-04-19
Thanks for taking time to answer. Here is the output.

```
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x71),  ISO_Level3_Shift (0x7c)
```

---

### Post by bingoUV on 2008-04-20
Super_R is not one of the super keys. Try running this 
```

xmodmap -e "add mod4 = Super_R"

```

The above command only changes the behaviour temporarily, a ctrl-alt-backspace or a reboot will revert the changes. After running the command, check whether both super keys are working. If yes, put the command at the end of the fle ~/.xsession (create the file if not present). If not, we will have to try something else.

Also check that in your keyboard settings (something like System -> hardware -> keyboard -> layout options) , under "Alt/Win key behavior", "Super is mapped to the Win-keys" is checked.

---

### Post by ramkumail on 2008-04-20
no luck. The problem remains even after running the command.(still no terminal command defined error appears on a dialog box immediately after pressing left windows key).
I as well selected  the option 'super key is mapped to win key in system-> preferences-> keyboard->layout tab->alt/win key behavior. still no luck. please advise me on the next course of action. I dont understand one thing. both the super keys work nicely if i switch on compiz-fusion. Left super key alone gives error as soon as i start metacity. Just mentioning it in case you had missed in the previous post.

---

### Post by bingoUV on 2008-04-20
Was metacity running when you ran the command xmodmap, or compiz? Does it give the same output in both?

---

### Post by ramkumail on 2008-05-12
sorry for the late reply. Yes. It gives the same output when metacity and compiz are running. What can be the problem?

---

### Post by Egils on 2008-05-16
You might find that the problem has to do with a compiz setting, even when you are using metacity - (on a different distribution) I was getting the same error message that you mentioned in your first post even when not using compiz because the run terminal command hadn't been defined in my compiz settings (in General Options > Commands > Run terminal command).

---

### Post by ramkumail on 2008-05-19
> **Egils said:**
> You might find that the problem has to do with a compiz setting, even when you are using metacity - (on a different distribution) I was getting the same error message that you mentioned in your first post even when not using compiz because the run terminal command hadn't been defined in my compiz settings (in General Options > Commands > Run terminal command).
Thanks for the reply.It gave me a hint to solve the problem. I checked in the place you mentioned. It is defined as > gnome-terminal in there which i guess is correct.  When i go to keyboard shortcuts and try to specify a keyboard shortcut using any of my super keys it comes as Mod4. After I changed my shortcut to start terminal in to > Mod4+T the problem got corrected. Now whenever i press super+T it shows as > No terminal command has been defined which is far less annoying and 'Gnome-Do' starts with both of the super keys. Thnks for all the people who helped especially bingoUV and Egils.
 Now I need to know whether can i leave the Mod4 problem or should i correct it by some means. If I have to correct it, how can i corect it.

---

