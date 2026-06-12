---
title: "Synaptic not working"
date: 2007-06-15
forum: General Help
---

### Post by Javier Carrera on 2007-06-15
Greetings from Ecuador.
I have been a happy user of Ubuntu Dapper for 6 months now. 3 weeks ago I made an installation of Feisty from 0, formating disks. Since then I don't get Synaptic to work. Whenever I try to do something, it just disappears. Running it from console, I got this message when it closed:

(synaptic:11528): XML-CRITICAL **: Document is empty

(synaptic:11528): XML-CRITICAL **: Start tag expected, '<' not found

(synaptic:11528): GLib-CRITICAL **: g_string_free: assertion `string != NULL' failed

(synaptic:11528): libglade-WARNING **: did not finish in PARSER_FINISH state
synaptic: rggladewindow.cc:59: RGGladeWindow::RGGladeWindow(RGWindow*, std::string, std::string): Assertion `_gladeXML' failed.
Cancelado (core dumped)

The controler for installing the video driver and the normal installer of Ubuntu are not working. I installed Automatix to try to find some of the software I need, and it is working fine.

In other forums it was recomended to make a new instalation of synaptic. What do you think?

Thank you.

---

### Post by jimbob on 2007-06-15
You can try removing it and re-installing to see if that helps:
 
    apt-get remove --purge synaptic
    apt-get install synaptic
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Javier Carrera on 2007-06-15
Problem solved following your directions. Thank you very much.

---

### Post by neilg4rqn on 2008-05-02
[QUOTE=jimbob;2851686]You can try removing it and re-installing to see if that helps:
 
    apt-get remove --purge synaptic
    apt-get install synaptic
________________________________       
  If I can't be Mr. Root I won't play ...

My synaptic wouldn't always run when I clicked on the menu entry - the timer would appear and then stop, all appeared normal apart from the fact that synaptic wasn't running. Following the un/reinstall routine  which seems to have worked I have now lost add/remove from my applications menu ???? Help
Confused of K/L

---

### Post by jimbob on 2008-05-02
Right click on main menu icon.  Click edit menus.  Make sure the Add/Remove selection is checked.

---

### Post by neilg4rqn on 2008-05-02
One tiny problem there jimbob - i don't appear to have that selection available anymore...

---

### Post by jimbob on 2008-05-02
Then go back into the same menu and click New Item.  Then fill in the four selections thusly:

  Type: Application
  Description:  Add/Remove
  Command: /usr/bin/gnome-app-install
  Comment: Install and remove applications

---

### Post by neilg4rqn on 2008-05-02
Sorry but I now get the following responce
Failed to execute child process "/usr/bin/gnome-app-install" (No such file or directory)
So I assume something is missing.
Thanks for your help so far.

---

### Post by dburnett77 on 2008-05-02
Similar circumstance here; got good luck with apt-get in superuser mode.

apt-get update often, and always remember searching is via asterisk, end.

ie, text* will yield all files with the word "text" in them.

---

### Post by jimbob on 2008-05-03
Go ahead and install that missing gnome app from a terminal with ***[COLOR="RoyalBlue"]sudo apt-get install gnome-app-install[/COLOR]***

Hopefully it will also add that menu item for you.

---

### Post by neilg4rqn on 2008-05-03
Thank you very much jimbob for curing that problem. Now what are you like on slow or non-responsive menus?

---

### Post by jimbob on 2008-05-03
Go ahead and open a new post about that since we are in the archive section right now and it is disallowed here.

Try to be a litle more specific about the the problem in your post such as which version you are running, etc, etc.
  
Glad this one worked out for you.

---

