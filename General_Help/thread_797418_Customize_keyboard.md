---
title: "Customize keyboard"
date: 2008-05-17
forum: General Help
---

### Post by chejose on 2008-05-17
I recently bought a new keyboard, and the "Insert" key is in a very bothersome place. I often hit it by mistake, and have then to go back and correct what I was working on.

I remember when I used Windows that there was a little program that allowed you to program the keys... for example, change "Insert" to "shift".

Would there be such a thing for ubuntu - Gnome?

I am running the 7.10 version.

Thanks,

José

---

### Post by Tiemen on 2008-05-17
Have you tried System-Preferences-Keyboard Shortcuts,??
Tim

---

### Post by chejose on 2008-05-19
I looked at it, but did not see anything that could affect the "Insert" key. I may have missed something, but am still where I was.

Thanks

José

---

### Post by Urinemachine on 2008-05-19
If you do find out how to do what you want, please let me know!  I use a Mac keyboard on my PC and the Windows button and Alt button the left side are flip flopped on the Macs logic, so in windows I use a key remapper so I can ALT+D (address bar in firefox) and ALT+TAB more normally.  In Ubuntu, I can't figure out how to do this!

---

### Post by Forlong on 2008-05-19
Create your own Xmodmap:
```
xmodmap -pke > $HOME/.Xmodmap
```
then open it in a text editor, e.g.
```
gedit $HOME/.Xmodmap
```
Look for **Insert** and change it to something else.
E.g. changing **Insert** to **Menu** will open the context menu, every time you press the insert button.
To test the change, simply run
```
xmodmap $HOME/.Xmodmap
```

---

### Post by chejose on 2008-05-19
Your solution sounds good, but when I try it I get permission denied. Even using sudo.
So I tried using su, but it would not accept my password.. "authentication failure".
This is the first time I have tried to enter code and it was denied.

Any suggestion?

Thanks,  José

---

### Post by Forlong on 2008-05-19
Which of the commands gave you *permission denied*?


P.S. never use sudo on a command that doesn't require it (and you *know* it does)!

---

### Post by chejose on 2008-05-19
OK.., with sudo su the code was accepted.But this time it said home/.xmodmap no such file or directory

---

### Post by Forlong on 2008-05-19
You are not supposed to replace $HOME with /home

Just use the commands as they are.

---

### Post by chejose on 2008-05-19
Well, I am afraid that I am a bit slow on using code, but as I fussed with it, it now works. So many thanks for solving a frustrating problem.

José

---

### Post by chejose on 2008-05-23
Well, I thought I had this solved, but I am afraid not.

I can edit $HOME/.Xmodmap with no trouble. "Insert" (106) is now "Shift_R".

But today when I run xmodmap $HOME/Xmodmap the insert key does not change... in other words, it is still "Insert".

So I guess I am missing something here.

Thanks for patience.

José

---

### Post by Forlong on 2008-05-23
First of all, it's ```
xmodmap $HOME/.Xmodmap
```

And you shouldn't need to run this everytime on startup. GNOME should've asked you if you want to use the custom one.

---

### Post by chejose on 2008-05-23
Right, I'm sorry. I was using $HOME/.Xmodmap I just made a typing error above.

So after a reboot the choice did come up this time between two Xmodmap files, and I apparently chose the wrong one. I see now that I should have chosen the one with a ~ after it. In other words, the insert is still insert.

But now the choice is no longer offered. I edited .Xmodmap again with no changes yet the dialog box did not come up. So the question is how to get the new .Xmodmap file to be chosen.

Thanks for much patience.

José

---

### Post by Forlong on 2008-05-23
No, do not use the file with the ~ at the end. That is a backup file made by gEdit.

Bot you obviously changed something that made it stop working. Open both .Xomdmap and .Xmodmap~ and compare the two.

---

### Post by chejose on 2008-05-23
I opened the two, and they are the same. Both have Shift_L for key 106

---

### Post by Forlong on 2008-05-23
You can always test the results via ```
xmodmap $HOME/.Xmodmap
``` If this doesn't work as expected, then you have made something wrong... just fiddle with it, until it works how you like ;)

If all else fails, just remove the file(s) completely and start over.

---

### Post by chejose on 2008-05-23
OK... many thanks for your help. I will try removing everything and starting again.

José

---

