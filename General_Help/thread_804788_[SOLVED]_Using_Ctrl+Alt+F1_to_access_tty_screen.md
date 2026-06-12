---
title: "[SOLVED] Using Ctrl+Alt+F1 to access tty screen"
date: 2008-05-23
forum: General Help
---

### Post by ezramorris on 2008-05-23
If I press Ctrl+Alt+F1 whilst using the live cd or **booting** from the hard disk, I see the terminal screen, but I can't seem to access this through my installed version of Ubuntu.

Any ideas?

---

### Post by Slim Odds on 2008-05-23
> **ezramorris said:**
> If I press Ctrl+Alt+F1 whilst using the live cd or **booting**from the hard disk, I see the terminal screen, but I can't seem to access this through my installed version of Ubuntu.

Any ideas?

Can you clarify?    Live CD    or    installed version.

The Live CD is very different than an installed version when it comes to things like the TTYs

---

### Post by ezramorris on 2008-05-23
> **Slim Odds said:**
> Can you clarify?    Live CD    or    installed version.

The Live CD is very different than an installed version when it comes to things like the TTYs

Live CD works, Installed doesn't

---

### Post by mali2297 on 2008-05-23
How about **Ctrl+Alt+F2**? 

What is printed on the terminal screen?

---

### Post by ezramorris on 2008-05-23
> **mali2297 said:**
> How about **Ctrl+Alt+F2**? 

What is printed on the terminal screen?

Nope, none of them work.

I don't get a terminal screen, it just stays in X.

---

### Post by mali2297 on 2008-05-23
To rule out that it is a problem with the *F keys*, does **Alt+F2** open a run dialog?

---

### Post by ezramorris on 2008-05-23
> **mali2297 said:**
> To rule out that it is a problem with the *F keys*, does **Alt+F2** open a run dialog?

It did until I reconfigured the shortcuts, but Alt+F1 still opens the main menu.

---

### Post by mali2297 on 2008-05-23
Post the output of
```

xmodmap -pke | grep VT

```

---

### Post by ezramorris on 2008-05-23
> **mali2297 said:**
> Post the output of
```

xmodmap -pke | grep VT

```

ezra@ezra-laptop:~$ xmodmap -pke | grep VT
keycode  67 = F1 XF86_Switch_VT_1
keycode  68 = F2 XF86_Switch_VT_2
keycode  69 = F3 XF86_Switch_VT_3
keycode  70 = F4 XF86_Switch_VT_4
keycode  71 = F5 XF86_Switch_VT_5
keycode  72 = F6 XF86_Switch_VT_6
keycode  73 = F7 XF86_Switch_VT_7
keycode  74 = F8 XF86_Switch_VT_8
keycode  75 = F9 XF86_Switch_VT_9
keycode  76 = F10 XF86_Switch_VT_10
keycode  95 = F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12

---

### Post by mali2297 on 2008-05-23
Try changing to a tty from the command line:
```

sudo chvt 2

```

If that doesn't work, check
```

pgrep -l tty

```

---

### Post by ezramorris on 2008-05-23
> **mali2297 said:**
> Try changing to a tty from the command line:
```

sudo chvt 2

```

If that doesn't work, check
```

pgrep -l tty

```

```
sudo chvt 2
``` works, and I can change back to X with Ctrl-Alt-F7.

---

### Post by mali2297 on 2008-05-23
> **ezramorris said:**
> ```
sudo chvt 2
``` works, and I can change back to X with Ctrl-Alt-F7.

OK, then it must be something about the key mappings in X. 

What application do you use to set shortcuts? (Gnome configuration editor, Compiz settings manager or something else.) Is it possible that any of these redefines Ctrl+Alt+F1 etc?

You can also check the modifier keys with
```

xmodmap -pm

```

Do you experience any other peculiarities with regards to key mappings?
Does Ctrl+Alt+Backspace terminate the X session as it should?

---

### Post by ezramorris on 2008-05-23
> **mali2297 said:**
> OK, then it must be something about the key mappings in X. 

What application do you use to set shortcuts? (Gnome configuration editor, Compiz settings manager or something else.) Is it possible that any of these redefines Ctrl+Alt+F1 etc?

You can also check the modifier keys with
```

xmodmap -pm

```

Do you experience any other peculiarities with regards to key mappings?
Does Ctrl+Alt+Backspace terminate the X session as it should?

I use both the gnome config and compiz. There's not a lot in gnome, and nothing with ctrl-alt-f*. Had a look at compiz, but it appears it doesn't let you use ctrl-alt-f* for anything. Also tried disabling compiz, but this didn't help.

xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x71),  ISO_Level3_Shift (0x7c)

There is a feature of compiz which lets you assign a command to a keyboard shortcut. I could do this with chvt as a last resort.

---

### Post by mali2297 on 2008-05-23
Another thing that you can check is the log for the X session:
```

egrep "EE|WW" /var/log/Xorg.0.log

```

---

### Post by wootah on 2008-05-23
Just a quick side note while we are on the topic of TTYs: Is it possible to change the screen resolution of the TTY with 7.10, kernel 2.6.22-14 ? Also, do you folks know how to add a watermarked graphic to the TTY (like Suse has with the penguin in the top left) ?

---

### Post by ezramorris on 2008-05-23
> **mali2297 said:**
> Another thing that you can check is the log for the X session:
```

egrep "EE|WW" /var/log/Xorg.0.log

```

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): could not detect X server version (query_status=-3)
(WW) fglrx(0): Option "UseFBDev" is not used
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
---snip---
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(WW) Configured Mouse: No Device specified, looking for one...

---

### Post by mali2297 on 2008-05-24
I'm running out of ideas, none of the outputs gives me a clue about the cause of the problem.

A little search in the forums lead me to these related threads:

[http://ubuntuforums.org/showthread.php?t=472647?post=#10](http://ubuntuforums.org/showthread.php?t=472647?post=#10)
[http://ubuntuforums.org/showthread.php?p=4671032](http://ubuntuforums.org/showthread.php?p=4671032)

Perhaps you can try reinstalling **xkb-data**.

---

### Post by ezramorris on 2008-05-24
> **mali2297 said:**
> I'm running out of ideas, none of the outputs gives me a clue about the cause of the problem.

A little search in the forums lead me to these related threads:

[http://ubuntuforums.org/showthread.php?t=472647?post=#10](http://ubuntuforums.org/showthread.php?t=472647?post=#10)
[http://ubuntuforums.org/showthread.php?p=4671032](http://ubuntuforums.org/showthread.php?p=4671032)

Perhaps you can try reinstalling **xkb-data**.

Thanks for all your posts. I tried all the suggestions, but no,luck.

---

### Post by mali2297 on 2008-05-30
> **ezramorris said:**
> Thanks for all your posts. I tried all the suggestions, but no,luck.

Wait, I've got a few more ideas now...

A possible solution to your problem might be to change "uk" in xorg.conf to "gb". That is, open the file with
```

gksudo gedit /etc/X11/xorg.conf

```
and change 
```

Option "XkbLayout" "uk"

```
to
```

Option "XkbLayout" "gb"

```

If that doesn't work, [this]("http://ubuntuforums.org/showpost.php?p=5077985&postcount=9") might.

---

### Post by ezramorris on 2008-05-30
> **mali2297 said:**
> Wait, I've got a few more ideas now...

A possible solution to your problem might be to change "uk" in xorg.conf to "gb". That is, open the file with
```

gksudo gedit /etc/X11/xorg.conf

```
and change 
```

Option "XkbLayout" "uk"

```
to
```

Option "XkbLayout" "gb"

```

If that doesn't work, [this]("http://ubuntuforums.org/showpost.php?p=5077985&postcount=9") might.

Worked like a charm. Thanks a lot.

---

### Post by Nameless_one on 2008-06-25
I have also got this problem. However, I use two layouts: us and gr (not uk). 

I reinstalled xkb-data and rebooted, but that didn't work. 

Also, the virtual terminals are running, pgrep shows six of them (as you'd expect), and I can switch into them with sudo chvt (and Ctrl+Alt+F7 works, if I want to return to X). 

However, xmodmap reports:

```
keycode  67 = F1 F1 
keycode  68 = F2 F2
keycode  69 = F3 F3
keycode  70 = F4 F4
keycode  71 = F5 F5
keycode  72 = F6 F6
keycode  73 = F7 F7
keycode  74 = F8 F8
keycode  75 = F9 F9
keycode  76 = F10 F10
```

I don't seem to have the shortcuts to switch to virtual terminals configured. I read a bit on xmodmap, tried a couple of things, but none of them work. Currently, for example, I have turned ```
keycode 67 = F1 F1
``` to ```
keycode  67 = F1 F1 NoSymbol XF86_Switch_VT_1
```, but still Ctrl+Alt+F1 does nothing. 

By the way, isn't the XF86_Switch_VT_1 string supposed to go in the fourth place, which maps the function of the key, plus the two modifiers? I also tried keycode 67 = F1 XF86_Switch_VT_1, but that didn't work either.

---

### Post by mali2297 on 2008-06-25
> **Nameless_one said:**
> 
By the way, isn't the XF86_Switch_VT_1 string supposed to go in the fourth place, which maps the function of the key, plus the two modifiers? I also tried keycode 67 = F1 XF86_Switch_VT_1, but that didn't work either.

My xmodmap is like in post #9. Are you're sure that the new key binding has been read? Check *xmodmap -pke | grep VT* again.

---

### Post by Nameless_one on 2008-06-25
I just changed it to keycode 67 = F1 XF86_Switch_VT_1, ran xmodmap to confirm that it was OK (it was), and pressed Ctrl+Alt+F1. Nothing happened.

EDIT: Btw, I think I was right before when I said that it shouldn't be keycode 67 = F1 XF86_Switch_VT_1 because in the second place, is the function that is executed when the base key is modified by Shift. Proof: Shift+F1 now brings me to tty1. And I also must have done something wring with my key mappings because switching layouts broke a bit.

---

### Post by brendanpiater on 2008-08-02
Worked for me to, thx!

---

