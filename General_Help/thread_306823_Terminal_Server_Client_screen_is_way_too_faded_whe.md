---
title: "Terminal Server Client screen is way too faded when Beryl is on"
date: 2006-11-25
forum: General Help
---

### Post by kimro on 2006-11-25
My Terminal Server Client screen is way too faded when Beryl is enabled.
If someone can point me to the right direction in attempting to solve this problem, it would be greatly appreciated. Thank you in advance.

---

### Post by DimitrisC on 2006-11-25
Had the same problem with a lot of applications (like frozen bubble, gxmame) as well as terminal server.  It seems that beryl makes some application look transparent.

Try starting terminal server (and any other application that gives you this problem) like this:

   XLIB_SKIP_ARGB_VISUALS=1 tsclient

If this works you can create a script for the applications that need this.
e.g:

#!/bin/bash
XLIB_SKIP_ARGB_VISUALS=1 frozen-bubble

and make it executable: chmod +x name_of_script

It worked for me i hope it helps!

---

### Post by kimro on 2006-11-25
Thanks!! 

One more question.. is there a way to modify the menu so it executes the line you specified instead of whatever the default it is for terminal server client (tsclient)?

---

### Post by DimitrisC on 2006-11-25
You can change the terminal server shortcut in the menu with alacarte menu editor.  Open the editor find the terminal server entry and in properties change the command entry to point to the script you created above instead of tsclient.

---

### Post by kimro on 2006-11-25
This is a n00b questions but I am really a noob so I'll ask away...
Is alacarte installed by default on Edgy or do I have to download it? Thank you!!!

---

### Post by DimitrisC on 2006-11-25
Don't worry about it! You can ask anything you want :D 

If i remember correctly in edgy alacarte menu editor its not in the menu. (In dapper you can find it in system tools).

I believe its already installed by default in edgy too but its not visible in the menu (don't know why).  Open a terminal and write alacarte.

That should start alacarte menu editor.

---

### Post by kimro on 2006-11-25
Thanks!!! Got everything working by creating a script to run tsclient as you advised and then changing the menu to run it using alacarte.

:-D

---

### Post by gushy on 2007-01-31
Excellent, that's fixed the problem for me too. Thanks.

Changed my menu entry which is great; if only it fixed the tsclient panel applet .... if anyone finds a solution to the applet, please post it.

---

