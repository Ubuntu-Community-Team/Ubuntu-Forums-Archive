---
title: "No window manager running"
date: 2008-06-22
forum: General Help
---

### Post by manoka on 2008-06-22
Hello,
The signs for the window commands, like "Minimize", "Close" etc., have disappeared. The browser window is covering - though not always - the top line with the "Applications", "Places", "System" etc., the bottom line only shows the trash and the "Hide all windows and show the desktop" signs, and when I click on the latter, I'm getting the message, that I'm not running a window manager. 
After a recent online upgrade to Ubuntu 7.10, I'm now using that troublesome version.
Any proposals for a solution would be very much appreciated.
Thanks
manoka

---

### Post by linfidel on 2008-06-22
Try opening a terminal and typing
metacity --replace

For more information, try this article:
[http://asktheadmin.wordpress.com/2008/05/01/ubuntu-quick-tip-missing-minimize-and-maximize-window-buttons/](http://asktheadmin.wordpress.com/2008/05/01/ubuntu-quick-tip-missing-minimize-and-maximize-window-buttons/)

If you are running a different window manager, substitute its name for metacity.

---

### Post by manoka on 2008-06-22
Actually I haven't got a clue which window manager I have got. Today is the first time I have ever read of such a manager. 
Where would I find info about which window manager I'm running?
And is "metacity -replace" the complete command line, or is there a "sudo" or something going in front of it? Please give the complete line to a newbie.
Actually this makes me wonder, whether it will know with what it has to replace it and where to find that.

---

### Post by linfidel on 2008-06-22
> **manoka said:**
> Actually I haven't got a clue which window manager I have got. Today is the first time I have ever read of such a manager. 
Where would I find info about which window manager I'm running?
And is "metacity -replace" the complete command line, or is there a "sudo" or something going in front of it? Please give the complete line to a newbie.
Actually this makes me wonder, whether it will know with what it has to replace it and where to find that.Sorry if I was too vague - I thought the link might help if you wanted to know more, but I realize it can be a little overwhelming.

metacity if the default window manager for gnome, the display manager.  The window manager just does the window placement, decorations (titlebar and frame) and the window controls.  It talks to gnome to get things done.  

Then there's compiz fusion, which is the display manager for the 3D desktop effects.  If you're using the fancier effects, you can try compiz --replace.  I believe compiz does the window management, too.  But, it's possible you could be using emerald with compiz, although if you were, you'd probably know.  It does the fancy themes for compiz.

You simply need to type the command in the terminal.  It won't hurt anything.  If something goes wrong, you can always press Ctrl-alt-Backspace, which will reload the x-windows system.  But don't do that without saving data, as it will close all the x-windows apps (graphical apps) ungracefully.

If you restart and have the same problem, you may need to save your configuration after typing the command (assuming it works).  To do this, open the menu "System/Preferences/Sessions", then open the Session Options tab, and press "Remember currently running applications".

---

