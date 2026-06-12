---
title: "sudo stopped working temporarly"
date: 2007-09-24
forum: General Help
---

### Post by Nevermore on 2007-09-24
Hi everyone
i have been using my ubuntu server for over 300 hours when this problem appeared:
i was trying to access it tru ssh, in order to scp some stuffs
i noticed that i was unable to get in, but i got only a connection reset by peer
so i turned on the server monitor and gave a fast look:
[LIST=1]
[*]gnome was on and working correctly
[*]terminal pop up correctly and runs command
[*]sudo command in terminal doesn't do anything else than hanging
[*]ctrl-alt-f2 and tried to login in cli, login hangs
[*]sudo reboot hangs
[*]sudo shutdown now hangs
[*]trying to reboot from gnome fails
[*]ctrl-alt-backspace but xorg doesnt restart nor i have a terminal
[/LIST]
i had to do an hard reboot in order to regain control of the pc
what did it happen? where should i check what happened?
any idea?
i can't afford this to happen again since i was lucky i was at home, but if i am in remote, how can i hard reboot the computer?
thanks

---

### Post by p_quarles on 2007-09-24
One thing that needs to be said here is that a server running a GUI isn't going to be nearly as stable as one that isn't. If you need guaranteed remote access, I would either get rid of X, or install a lighter, more stable window manager (Openbox, maybe). 

That said, if I were you I would take a close look at my auth.log files, and scan for any errors or suspicious activity.

---

### Post by Nevermore on 2007-09-25
what i noticed is that this kind problem never happened when i was not logged in..
i left the server for more than 30 days on gdm screen and everything went fine..
but sometime i need to use X.
one example for all:
deluge
all my investigations on logs were totally vain, couldnt find anything that could have caused the problem

---

