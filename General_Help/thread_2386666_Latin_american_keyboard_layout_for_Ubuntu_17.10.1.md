---
title: "Latin american keyboard layout for Ubuntu 17.10.1"
date: 2018-03-08
forum: General Help
---

### Post by klus-spam on 2018-03-08
Hi there,

I just set up completely from cero my laptop and therefore installed Ubuntu 17.10.1 from scratch.
Before, I had a Spanish (latin american) keyboard layout installed. I believe I have not reinstalled my laptop since 14.04 or something like that.

Now, in the settings are "normal" spanish keyboards, but latin american layout is nowhere to find. At least I do not find it.

Maybe someone has an idea how to install it.

Thanks and regards,
Sebastian

---

### Post by #&amp;thj^% on 2018-03-08
Some rarely used keyboard layout variants are not available by default when you click the + button. To make also those input sources available you can open a terminal window by pressing Ctrl + Alt + T and run this command:
```

gsettings set org.gnome.desktop.input-sources show-all-sources true
```
Dose it show now?

---

### Post by klus-spam on 2018-03-09
Hi @1fallen,

I read that somewhere in one of the forums. No luck unfortunately :(

Regards,
Sebastian

---

### Post by #&amp;thj^% on 2018-03-09
Are you sure you looked in the right spot?
I'm on XFCE DE

---

### Post by klus-spam on 2018-03-09
Well - quite sure.  I am attaching some screenshots of what I see.

There are certainly more spanish layouts, but no latin american. Neither under Spanish, nor under latin american. Sorry for the german interface.  

  [ATTACH=CONFIG]278879[/ATTACH][ATTACH=CONFIG]278880[/ATTACH]

BTW: I would have no problem to install the keyboard through terminal. I just do not know how.
Thanks,
Sebastian

---

### Post by #&amp;thj^% on 2018-03-09
> **klus-spam said:**
> Well - quite sure.  I am attaching some screenshots of what I see.

There are certainly more spanish layouts, but no latin american. Neither under Spanish, nor under latin american. Sorry for the german interface.  

  [ATTACH=CONFIG]278879[/ATTACH][ATTACH=CONFIG]278880[/ATTACH]

BTW: I would have no problem to install the keyboard through terminal. I just do not know how.
Thanks,
Sebastian

Well now you got me thinking///?
I just keep rolling my OS's>> but I would have to think that would be overwritten with the changes;:confused:
**See my edit:**
Or show this:
```
cd /usr/share/X11/xkb/symbols && ls
```

 
It's been a while since I have installed keyboard layouts via cli.
EDIT Ah Ha! I now figured out why I keep extra layouts>> they are stored in "**/usr/share/X11/xkb/symbols**"
And I always have a copy (backup) of both "/usr/share/X11/xkb/symbols" and "/etc/X11" among others that I keep stored if needed.
And the one we want here for you is "latam"

---

### Post by #&amp;thj^% on 2018-03-10
He He He! I'll bet steeldriver is just setting behind his monitor laughing up a storm.
The easiest way to this via terminal:
```
sudo apt-get install console-common

```
Now we set it (or try ;)) with:
```
sudo dpkg-reconfigure console-data
```
A window will appear in the terminal>>>now select "select keymap from full list" tab to ok>> now arrow down to **"pc /qwerty /US american/Standard/with latin1"** again tab down to "ok" Bam there you go should now show and select with:
```
sudo dpkg-reconfigure keyboard-configuration
```
Select the keybord you have now make, model, tab to "ok"
now find your American Latin tab "ok" and there you have it.
Screenshots included.
easy peasy, nothing to it!  :lolflag:

---

### Post by klus-spam on 2018-03-11
I am afraid I will have to stretch your skills a little more :p

Just did it the easy-peasy way and everything went exactly as described. Just a little side-effect: nothing changed at all. I'm still stuck to the US keyboard layout. :confused:
Tried to log on and off again, but no result.

Sorry for bothering...

Regards,
Sebastian

---

### Post by klus-spam on 2018-03-11
This is my output of 

```
 	cd /usr/share/X11/xkb/symbols && ls
```

[ATTACH=CONFIG]278900[/ATTACH]

I might have a backup of the folders you cited. From my previous installation. Not sure if I could re-use them here on 17.10

Regards,
Sebastian

---

### Post by klus-spam on 2018-03-11
Got it!!!
Here's what I did:


[LIST]
[*]From the settings, open "Region and Languages".
[*]Make sure you have "Spanish" installed (for my case).
[*]Switch to the "Regional formats" tab.
[*]Select "Spanish (Costa Rica)".
[*]Confirm all open windows and **Log off**!
[*]Log on again, and go back to "Region and Languages".
[*]Click the plus (+) sign in order to add a new input method.
[*]Now suddenly "Spanish (latin american)" comes up in the available keyboard layout list
[/LIST]

What I cannot confirm at this point is if any of the previous steps described by you (like installing console-common or setting the gnome input-sources to true) also impacted. I would at least suppose that setting the input-sources to true, did.

Thanks for all the help!

Regards,
Sebastian

---

### Post by #&amp;thj^% on 2018-03-11
Yes I kind of figured it would be a bit different for you!
And the easy peasy was an attempted joke as to the difficulty it was to achieve! :D
Good News though in the **upcoming 18.04 LTS** it is as easy as just using:
```
sudo dpkg-reconfigure keyboard-configuration
```
And you know the rest. ;)
Happy to hear you got it sorted.
Kind Regards

---

### Post by klus-spam on 2018-03-15
Thanks again for all the help @1fallen !

---

