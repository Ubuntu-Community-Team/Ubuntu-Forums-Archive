---
title: "Terminal Will Not Work"
date: 2008-01-01
forum: General Help
---

### Post by mindalchemist on 2008-01-01
Hi all,
I can not getting my terminal working.  I tried Alt + F2 and nothing.  This is what happens:

1.Click on Terminal Screen either turns to bootloading screen or entire screen becomes rainbow like lines.
2. Goes to logon page.

It is as if it restarts itself.  I tried this in the Live CD and it does the same thing.  I use Xubuntu 7.10.

Please help.

---

### Post by dlegend on 2008-01-01
Try doing these commands in a standard terminal (xterm, gnome-terminal, etc..):

```

sudo modprobe vga16fb
sudo modprobe fbcon

```

Now try and go back into the virtual terminal. If it works then:

Go to your /etc/modules file and edit it. Add **vga16fb** and **fbcon** as separate lines at the end of the file. This will have the modules automatically load on startup.

See this thread for more info (it is listed in the "Known gutsy bugs and workarounds thread"): [http://ubuntuforums.org/showthread.php?t=582962](http://ubuntuforums.org/showthread.php?t=582962)

Let me know if this works.

---

### Post by mindalchemist on 2008-01-01
Ummm and how do I get to something that I can do this at?  I have no access to a terminal.  I'll click Applications >Accessories > Terminal and nothing.

---

### Post by RC Howe on 2008-01-01
When you said ALT+F2, did you mean CTRL+ALT+F2? If not try CTRL+ALT+F1, or recovery mode.

Sorry if I am being obtuse, I just did not completely understand your problem, besides not being able to open a terminal from the Applications menu.

---

### Post by jken146 on 2008-01-01
Can you get to the virtual terminals Ctrl+Alt+F1 through to F6?  (Ctrl+Alt+F7 brings you back to the GUI)

---

### Post by dlegend on 2008-01-01
> **mindalchemist said:**
> Ummm and how do I get to something that I can do this at?  I have no access to a terminal.  I'll click Applications >Accessories > Terminal and nothing.

Oh sorry my mistake. I thought you were talking about the *virtual terminal*. So when you press Alt + F2, do you get the run application dialog to appear? If it does, try **sudo apt-get install gnome-terminal** and see if you can run gnome-terminal. 

I don't think I have a solution to this so you might need to do some googling or wait until someone else responds. It'd just be nice for anyone helping to have more information about your problem.

---

### Post by mindalchemist on 2008-01-01
> **dlegend said:**
> Oh sorry my mistake. I thought you were talking about the *virtual terminal*. So when you press Alt + F2, do you get the run application dialog to appear? If it does, try **sudo apt-get install gnome-terminal** and see if you can run gnome-terminal. 

I don't think I have a solution to this so you might need to do some googling or wait until someone else responds. It'd just be nice for anyone helping to have more information about your problem.

I am able to use the terminals on Ctrl + Alt +F1-6 but the one on the Applications still a no.  Can't the terminals on F1-6 do the same thing as the one under Applications?

---

### Post by jken146 on 2008-01-01
Try using one of those terminals (tty1-6) to install gnome-terminal.

```
sudo apt-get install gnome-terminal
```

Then Ctrl+Alt+F7 and see if you can run the terminal from the menu.

---

### Post by dlegend on 2008-01-01
> **mindalchemist said:**
> I am able to use the terminals on Ctrl + Alt +F1-6 but the one on the Applications still a no.  Can't the terminals on F1-6 do the same thing as the one under Applications?

Yeah they can. If the xfce terminal doesn't work you might want to try the command I mentioned earlier -- **sudo apt-get install gnome-terminal** through the virtual terminal (Ctrl+Alt F1-6 then Ctrl+Alt+F7 to get back) or if you can find another terminal to install by all means try. This won't solve your terminal not working issue but it would be interesting to know if other terminals function properly. 

After you've installed the gnome-terminal though just access it through your menu or launch it by typing in gnome-terminal after it has installed.

I personally use gnome so don't know a lot about xfce (though I have it installed) so I won't be of too much help to you getting the actual default xfce terminal to work.

---

### Post by mindalchemist on 2008-01-01
> **dlegend said:**
> Yeah they can. If the xfce terminal doesn't work you might want to try the command I mentioned earlier -- **sudo apt-get install gnome-terminal** through the virtual terminal (Ctrl+Alt F1-6 then Ctrl+Alt+F7 to get back) or if you can find another terminal to install by all means try. This won't solve your terminal not working issue but it would be interesting to know if other terminals function properly.

I personally use gnome so don't know a lot about xfce (though I have it installed) so I won't be of too much help to you getting the actual default xfce terminal to work.

I did that command.  Where does gnome-terminal install to? Anotherwords, where can I select it?

---

### Post by jken146 on 2008-01-01
For some reason I assumed you were on Gnome.  Duh!

Try launching (with alt+F2) **xfce4-terminal**

Also try **xterm** (I'm not sure if this is installed by default -- you can always install it).

You can install gnome-terminal if neither of those works.  Also look in Add/Remove or Synaptic -- there are plenty more terminal emulators you could try installing.

---

### Post by jken146 on 2008-01-01
As for launching gnome-terminal, hit Alt+F2 and type in **gnome-terminal**.  I'd have thought it would be in the menus though.

---

### Post by dlegend on 2008-01-01
> **mindalchemist said:**
> I did that command.  Where does gnome-terminal install to? Anotherwords, where can I select it?

To run it just go into the virtual terminal and type in **gnome-terminal** -- I think it will launch when you leave the virtual terminal. If not just try Alt+F2 and typing in **gnome-terminal** as the command.

---

### Post by mindalchemist on 2008-01-02
Update: I have the gnome terminal working so I will just use that from now on.  I do have a shortcut of it on my desktop but not in the Applications menu.

---

### Post by rowanparker on 2008-01-02
> **mindalchemist said:**
> Update: I have the gnome terminal working so I will just use that from now on.  I do have a shortcut of it on my desktop but not in the Applications menu.
Edit your menu to the correct command (the one in your shortcut on your desktop).

---

