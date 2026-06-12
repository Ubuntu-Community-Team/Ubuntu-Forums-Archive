---
title: "[SOLVED] Change keyboard layout problem"
date: 2008-05-18
forum: General Help
---

### Post by Tryfon on 2008-05-18
Please someone help me with this, because I have no idea what to do:

I've configured the keyboard layout to switch layouts between English and Greek with the combination Alt+Shift I was used to since Windows. Everything worked flawlessly until I updated to Hardy. Now the combination doesn't work unless I go to System->Preferences->Keyboard->Layouts->Layout Options->Layout switching and uncheck and recheck the Alt+Shift checkbox, every time I start up my PC.
Any idea?

---

### Post by highstead on 2008-05-18
Having a similiar problem.  Every boot it keeps defaulting to QWERTY even though i don't have that as an option for a layout.

---

### Post by strabes on 2008-05-18
Having the same problem on my parents' computer.

---

### Post by TeoBigusGeekus on 2008-05-18
> **Tryfon said:**
> Please someone help me with this, because I have no idea what to do:

I've configured the keyboard layout to switch layouts between English and Greek with the combination Alt+Shift I was used to since Windows. Everything worked flawlessly until I updated to Hardy. Now the combination doesn't work unless I go to System->Preferences->Keyboard->Layouts->Layout Options->Layout switching and uncheck and recheck the Alt+Shift checkbox, every time I start up my PC.
Any idea?

Jesus... So I'm not the only one...

---

### Post by volksstimme on 2008-05-18
Yeah, I, too, noticed the shortcuts didn't work (any of them, I tried enabling them all at the same time to no end) and nor does the DE keyboard layout (seems to act as though Alt Gr is pressed), though I think that's local to my computer, for whatever reason...

---

### Post by TeoBigusGeekus on 2008-05-18
It's a bug, reported just a couple of days ago.
[https://bugs.launchpad.net/ubuntu/+bug/231310]("https://bugs.launchpad.net/ubuntu/+bug/231310")

---

### Post by der_joachim on 2008-05-19
You can edit /etc/X11/xorg.conf by hand. Here's what to do:
- Open /etc/X11/xorg.conf . Please note that you need administrator privileges. Otherwise you will not be able to write any changes.
- Find your keyboard config. It should look somewhat like this:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

```
- To alternate between keyboard layouts (us and presumably greek, for the OP), change the XkbLayout line to something like this:
```

      Option "XkbLayout" "us,gr" 

```
- Add (or change) the following line. Note that this line should fall within the Section/EndSection pair:
```

 Option "XkbOptions" "grp:alt_shift_toggle"

```
If you already have a few XkbOptions, you can put commas between the options:
```

 Option	"XkbOptions" "grp:alt_shift_toggle,compose:ralt,altwin:super_win"

```
- Save your changes (have you made a backup?) and restart X.

You should now be able to toggle keyboard layouts by pressing Alt+Shift.

---

### Post by Tryfon on 2008-05-19
Thank you very much! Problem resolved!

---

### Post by TeoBigusGeekus on 2008-05-19
Kick @ss!!!
You're the man der_joachim!!!

---

### Post by muadnu on 2008-06-28
I'm seeing something weird. I added the relevant lines to my xorg.conf, bu when I turn on my comupter, the key combinations don't work. But if I restart X (ctrl+alt+backspace), they start working as they should. I'm not sure what could be causing this...

---

### Post by muadnu on 2008-07-29
I don't know if anyone's still interested in this, but here goes my workaround. The problem (at least in my case) seems to be related with using autologin (see [https://bugs.launchpad.net/bugs/196277]("https://bugs.launchpad.net/bugs/196277")). Disabling autologin seems to solve the issue. But if you want to keep using autologin there's an easy way to get layout switching working. Simply run 'setxkbmap' on a terminal to reset the key bindings and you are done. Or better, create a file with the following (one-line) script

```
sleep 25 && setxkbmap
```

and then add the script to gnome-session.

---

### Post by cika.mancic on 2008-08-13
Hi, i have a same problem. 
i just need for someone to tell me what's short for Serbian Latin, and Serbian (default)?? Or, where can I find that? Example: Greece - gr
Thanks!

---

### Post by cika.mancic on 2008-08-15
Someone... Please...
I need to restart without login cause of mine torrents, screenlets and etc. But then my keybord is buging!
help....

---

### Post by cika.mancic on 2008-08-15
For muadnu:
Can you guide me how to make script file as you said.

"Or better, create a file with the following (one-line) script

Code:

sleep 25 && setxkbmap"

and apply it.

Or help me do the reset the key bindings in "setxkbmap".
Thanks a lot, but i am new in linux, so try to be sistematic about it.
And sorry for my bad English...

---

### Post by muadnu on 2008-08-17
> **cika.mancic said:**
> For muadnu:
Can you guide me how to make script file as you said.

"Or better, create a file with the following (one-line) script


Sorry it took me longer than I expected, cika.mancic. Here it goes:

1. Open a text editor (Applications->Accesories->Text Editor in Gnome, or open a terminal and type "gedit", without the quotes). Then in an empty file add a single line with this in it:
```
sleep 25 && setxkbmap
```

2. Save the file to a directory of your choice (your home directory will work, which is /home/yourusername). Save it with the name "kbdfix.sh". Close the text editor.

3. In a terminal, go to the directory where you saved the file and type
```
chmod +x kbdfix.sh
```
If you don't like using the terminal, browse to the directory where you saved the file, find it, right-click it, choose properties, then go to the permissions tab, and make sure all the "execute" checkboxes are checked.

4. Finally, add this script to gnome-session. I'm assuming you are using Ubuntu and not Kubuntu or Xubuntu or any other. To do that, go to System->Preferences->Sessions, click on "add", enter "Layout switching fix" (or any other description you want), then click on "Browse" and look for the kbdfix.sh file in the directory you put it in.

That should make the trick. Next time you log in it should be working. Log out and then log back in to try it.

Hope it helps, let me know if something doesn't...

---

### Post by cika.mancic on 2008-08-18
BRAVO!
It works! :lolflag:
But, you have one misprint:
"3. In a terminal, go to the directory where you saved the file and type
Code:
chmod +x kbdfix.sh"
It should be:
chmod +x kdfix.sh
cause that what you told us to name the file.
With that fix it works like a charm!

---

### Post by muadnu on 2008-08-18
I actually meant for the file to be called kbdfix.sh, so the typo is in step 2. Glad it helped anyway!

---

### Post by poscaman on 2008-10-30
> **muadnu said:**
> Sorry it took me longer than I expected, cika.mancic. Here it goes:

1. Open a text editor (Applications->Accesories->Text Editor in Gnome, or open a terminal and type "gedit", without the quotes). Then in an empty file add a single line with this in it:
```
sleep 25 && setxkbmap
```

2. Save the file to a directory of your choice (your home directory will work, which is /home/yourusername). Save it with the name "kbdfix.sh". Close the text editor.

3. In a terminal, go to the directory where you saved the file and type
```
chmod +x kbdfix.sh
```
If you don't like using the terminal, browse to the directory where you saved the file, find it, right-click it, choose properties, then go to the permissions tab, and make sure all the "execute" checkboxes are checked.

4. Finally, add this script to gnome-session. I'm assuming you are using Ubuntu and not Kubuntu or Xubuntu or any other. To do that, go to System->Preferences->Sessions, click on "add", enter "Layout switching fix" (or any other description you want), then click on "Browse" and look for the kbdfix.sh file in the directory you put it in.

That should make the trick. Next time you log in it should be working. Log out and then log back in to try it.

Hope it helps, let me know if something doesn't...

thanks a lot.it worked like a charm

---

### Post by Johann-1.0 on 2010-05-14
Hello friends.
My question is: How can I know the tag for my keyboard? I think there would be a table listing kb tags...where can I find it?
For example:
latam= latin american keyboard
us= us keyboard
??= russian phonetic
??= russian standard
Thanks a lot for answering me.

P.S.: can you tell me the name of the buttons? I want to toggle using right alt + left alt...how can I do that.
Can you also tell me how can I do to activate the "less than/higher than" key? It does't work
I'm using Ubuntu 8.04 LTS in a Compaq Presario V2415la notebook

---

### Post by pktel on 2011-08-25
hi,


i have the same problem. when i choose my keyboard layout to be german (default usa), configuration is not saved after reboot. i have no xorg.conf file because i have version 11.04. can anyone tell me about the relevant  config file and what i have to change there?


thanks

---

