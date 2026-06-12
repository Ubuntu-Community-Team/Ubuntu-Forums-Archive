---
title: "Is there a way to script a detached ssh command"
date: 2013-04-22
forum: General Help
---

### Post by CaptainMark on 2013-04-22
I have a script which runs locally on my desktop, it sends a command over ssh to a remote server in the front room,
Is there a way for my desktop to detach from the server immediately after running the ssh command, leaving the server to finish the command in its own time and allowing me to switch the desktop off.

I'm familiar with the idea of running a long command over ssh and using the keyboard shortcut 'ctrl+z' followed by 'bg' and 'disown' this is essentialy the effect I'd like to achieve but as part of a script.

Thank you for any help
Regards
Mark

---

### Post by Habitual on 2013-04-22
[screen]("https://help.ubuntu.com/community/Screen") can do exactly that.

---

### Post by SeijiSensei on 2013-04-22
If the client runs the process on the server in background mode, by following the command with an ampersand ("&"), the client can disconnect immediately.

---

### Post by Lars Noodén on 2013-04-22
Instead of disown you can launch the script with [nohup](http://manpages.ubuntu.com/manpages/quantal/en/man1/nohup.1posix.html).  That does the same thing as disown, it ignores SIGHUP thereafter.  If you combine nohup with & as mentioned above, the script should survive disconnection just fine.

---

### Post by CaptainMark on 2013-04-22
Thanks for the responses, unfortunately using ampersands and nohup doesn't work, I could close the terminal fine but the command would just hang and freeze when I shut the desktop (client) down, something to do with a socket remaining open, I didn't fully understand why. But thanks Habitual I have used screen many times but never knew it could be started (therefore scripted) in detached mode,this is exactly what I need.

Regards 
Cap'n

---

