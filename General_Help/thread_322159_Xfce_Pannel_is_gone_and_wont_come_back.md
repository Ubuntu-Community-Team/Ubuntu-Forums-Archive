---
title: "Xfce Pannel is gone and wont come back"
date: 2006-12-20
forum: General Help
---

### Post by schluffs1 on 2006-12-20
Hello,

Since the last shutdown my Xfce-Pannel wont come back. 

If I trie to F2+Alt and type "xfce-panel" then a Message popps up and says:

**Failed to execute child process "xfce-panel" (No such file or directory)**


Can anybody help me?

---

### Post by schluffs1 on 2006-12-20
Does nobody know how do bring the standart pannel back to the desktop....isn't there any (simple) command to (re)start the Pannel?


thx!

---

### Post by samden on 2006-12-20
This won't be any help I think, but I'm having similar problems. When the panel disappears I can bring it back like you have tried to, but I have had Firefox disappear on me. Whenever I try to use it I get the same error message about child process couldn't be found or something. I have reinstalled firefox, so it is there, and I can open it when I find the correct file in Thunar and click on it, but XFCE doesn't know it exists. 

You could try reinstalling the panel through Synaptic? Remember you can right-click on the desktop to bring up your applications menu even if the panel doesn't exist.

I have no idea what the solution to this child process thing is, but it certainly isn't isolated to the panel. Sorry I am no help!

---

### Post by bedfojo on 2006-12-20
The command is:

xfce4-panel

Try that.

If it reappears and then vanishes when you close the terminal, do it again but leave the terminal open. Then reboot, keeping the terminal open and ensuring that the "save session" box is checked.

This worked for me.

---

### Post by psquared89 on 2008-07-14
You don't need to reboot. If you just open a shell and run the command, then the panel process is "owned" by that shell. When you kill a parent process (in this case the shell), all of its children (in this case the panel) are killed to.

What you need to do is type:

xfce4-panel &
disown %xfce4-panel

The & starts the panel as a background process (letting you type at the terminal still), and the disown command disowns the panel process from the terminal, so that when you close the terminal, you don't lose the panel.  (If you ever forget to start a command with &, you can also hit Ctrl-Z to STOP a running command, and then type "bg" to background the process, then disown the same way).

---

