---
title: "Terminal window (split)"
date: 2008-02-08
forum: General Help
---

### Post by podollb on 2008-02-08
I very often open more than one terminal window (and it generally in response to what I am doing in one terminal window). Is there any way to "split" the terminal window that you are currently using as to have another shell start up on the same host so you essentially have immediate access to an additional terminal with some keystroke. That would be SOOO handy!

---

### Post by mozetti on 2008-02-08
You can use tabs in the terminal.
```
Shift+Ctrl+T
```

gives you a new terminal tab.

Use your mouse to select the tab, or ```
Ctrl+PgUp
``` to go to the previous tab or ```
Ctrl+PgDn
``` to go to the next tab.

Finally, if you use Compiz-Fusion and the Compiz-Config-Settings-Manager then you ***might*** be able to set up rules so that one terminal opens on a specific workspace at a specific size and specific place, and a second terminal opens on the same workspace, at a specific size, and a specific place right next to it.

I say, "might", because right now I have a rule set up so my terminal window appears in the center of workspace 2, with no window decoration and 50% transparency -- looks pretty neat, with a translucent black box in the center of the workspace to enter CLI commands. I'm not sure how involved it would be to try to get two instances of terminal to behave differently, but it might be possible.

---

### Post by jrib on 2008-02-08
use screen:
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)
[http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)

You can split or create "tabbed" shells.

Try: ```
screen
```
Then 'ctrl-a c' to create a new shell.  'ctrl-a #' where # is a digit from 0-9 switches you to the #th shell.  So 'ctrl-a 0' would bring you back to the first shell and then 'ctrl-a 1' would bring you to the new one.

---

### Post by Andrew Stone on 2008-02-08
Here's a command that opens a single terminal and sshes to 6 different machines which appear one in each tab:

/usr/bin/gnome-terminal --window --command "ssh -X -A root@192.168.1.50" --tab --command "ssh -X -A root@192.168.1.51" --tab --command "ssh -X -A root@192.168.1.52" --tab --command "ssh -X -A root@192.168.1.53" --tab --command "ssh -X -A root@192.168.1.54" --tab --command "ssh -X -A root@192.168.1.55" &

Of course this command is set up to ssh into machines in my private network; but I'm sure with this template you can modify for your own fun and enjoyment.

I right click on the gnome panel->add to panel->custom application launcher.  Then put this in the "command" field, add a name and change the icon to add a panel icon that will open up a terminal with multiple tabs.

---

### Post by oldos2er on 2008-02-08
> **podollb said:**
> I very often open more than one terminal window (and it generally in response to what I am doing in one terminal window). Is there any way to "split" the terminal window that you are currently using as to have another shell start up on the same host so you essentially have immediate access to an additional terminal with some 
keystroke. That would be SOOO handy!

 Shift-Ctrl-T opens a new tab, Shift-Ctrl-N opens a new window. This assumes you're using gnome-terminal.

---

### Post by podollb on 2008-02-08
Yeah I've used the tabs before, I'm not a big fan, I guess what I was wondering about was a split screen like I mentioned. The point was want to have both visible at one time.

For example, if you had a terminal that is open, I want to do some keystroke to split the screen (so both are visible). Similar to how you can do such things in emacs.

---

### Post by powderhound99 on 2008-02-08
I would like to add that alt 1-9 switches tabs as well.

Also I was looking for the same; at one point I swear I'd seen it and I think it was a friend who is quite the programmer, I'm lead to believe it took quite a bit of hacking. What seems to work best for me is assigning hot keys to launch a terminal. I use shift alt t (the new tab is shift ctrl t) this seems to work well. On a side note there is an extension to split your tabs in Firefox.

---

### Post by fguilhon on 2008-04-17
You can use multi-gnome-terminal for that...

---

### Post by jrib on 2008-04-17
> **podollb said:**
> Yeah I've used the tabs before, I'm not a big fan, I guess what I was wondering about was a split screen like I mentioned. The point was want to have both visible at one time.

For example, if you had a terminal that is open, I want to do some keystroke to split the screen (so both are visible). Similar to how you can do such things in emacs.

screen does this.  From the man page:
C-a S       (split)       Split the current region into two new ones.

---

### Post by podollb on 2008-04-17
multi-gnome-terminal looks ideal!

---

