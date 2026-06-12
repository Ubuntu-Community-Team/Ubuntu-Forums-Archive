---
title: "[SOLVED] lowercase 'e' not appearing in terminal"
date: 2007-07-12
forum: General Help
---

### Post by hdshngout on 2007-07-12
When I go into the terminal and try to type a command which contains a lowercase 'e' nothing happens and I get an annoying beep from the computer (not the speakers).  Whats weird is outside the terminal the 'e' key works fine!  I have no idea if this is a bug, or something I did (although I haven't done much), or what the problem is.  Its rather annoying as quite a few commands contain that letter.  

I have even tried switching keyboards, restarting, and searching through knowledge bases and google-ing it and nothing has helped.

Anyone face this problem or know the solution.  (I'm rather new to Ubuntu  so any help would be greatly appreciated).



-Nick

---

### Post by angryfirelord on 2007-07-12
Try checking in your xorg to see if your keyboard model is set correctly. Since you can't use 'e', in gnome-terminal, type **sudo nautilus**. Navigate to /etc/X11 and double-click on your xorg.conf file. Scroll down to *Section "InputDevice"*. Change these two options to look like this:
```
Option          "XkbModel"      "pc104"
Option          "XkbLayout"     "us"

```
Reboot & try again. If you don't use a US keyboard, change the above to reflect that.

Does this bug appear only in gnome-terminal or in any terminal? (like when you hit Ctrl+Alt+F1)

---

### Post by hdshngout on 2007-07-12
when I tried Ctrl+Alt+F1, the 'e' character worked, but once I logged in as nick, it immediatly stopped working.  So apparently its not just the gnome-terminal.

EDIT: I tried those changes and it didn't work either.  One thing I did notice however, was the 'e' character worked before the 

nick@nicks-desktop:~$

appeared.  (eg, if I were to type before it that appeared).

---

### Post by jpeddicord on 2007-07-12
Strange, I've never heard of this happening before. I'm guessing it is a keyboard layout problem, but definitely not an X.org problem.

(Additional information discovered over Jabber: It only happens on his own user account, so it is probably something funky with a bash profile.)

Jacob

---

### Post by hdshngout on 2007-07-12
Well aparently, like Jacob said, it was only a single-user based problem, so I'll let it alone and go to a different account.  Thank you for your help, guys :)

---

### Post by angryfirelord on 2007-07-13
> **jacobmp92 said:**
> Strange, I've never heard of this happening before. I'm guessing it is a keyboard layout problem, but definitely not an X.org problem.

(Additional information discovered over Jabber: It only happens on his own user account, so it is probably something funky with a bash profile.)

Jacob

Ahh, well I first thought he meant he was having problems with gnome-terminal only.

If you still need that account, you can always try a different shell.

---

