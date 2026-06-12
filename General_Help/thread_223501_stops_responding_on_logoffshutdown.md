---
title: "stops responding on logoff/shutdown"
date: 2006-07-26
forum: General Help
---

### Post by shoofy on 2006-07-26
Hi,
I'm fairly new to Ubuntu and Linux in general, so forgive me if I say something wrong or dumb. I've been setting up and customizing my new Ubuntu install, and somehow over the course of this I seem to have corrupted something. I'm using Gnome and whenever I press the logoff button on the toolbar at the top (the one that looks like a door) and it lets me choose to logoff, hibernate, shut down, reboot, etc., regardless of which one I pick my system just sort of stops responding. My mouse still works fine, but clicking on things has no effect and mousing over things similarly does not cause the usual mouseover effects. And then the system just sits in that state indefinitely. If I do a ctrl-alt-backspace it takes me back to the login screen and I can login right back to the non-responsive screen. I can shutdown from the login screen successfully. I can also run the shutdown command by doing a ctrl-alt-f1 and sudo shutdown -r now. I would very much like to make the shutdown/logoff process work correctly through the gui though. Can anyone help me fix it?

---

### Post by jordilin on 2006-07-26
I has happened to me two times when trying to shut down my system. It just freezed. I suspected that it was due to the fact that the os was doing some admin task such as a cron job or sth and at the very moment of shutting it down it freezed. But, I'm surprised that in your case always happen. Look around system logs such as /var/log/messages or syslog and tell us sth.

---

### Post by shoofy on 2006-07-27
The only thing that caught my eye as suspicious in syslog was:

Jul 25 18:00:14 localhost shutdown[7460]: shutting down for system reboot
Jul 25 18:00:15 localhost init: Switching to runlevel: 6
Jul 25 18:00:17 localhost kernel: [66746.284000] [fglrx:firegl_rmmap] *ERROR* map 0xdfbde950 still in use (map_count=1)
Jul 25 18:00:17 localhost kernel: [66746.324000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfbde940 still mapped
Jul 25 18:00:17 localhost kernel: [66746.356000] [fglrx:firegl_rmmap] *ERROR* map 0xdfba1650 still in use (map_count=1)
Jul 25 18:00:17 localhost kernel: [66746.384000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfba1640 still mapped
Jul 25 18:00:17 localhost kernel: [66746.416000] [fglrx:firegl_rmmap] *ERROR* map 0xdfbdea50 still in use (map_count=1)
Jul 25 18:00:17 localhost kernel: [66746.448000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfbdea40 still mapped

right after the reboot command came in. What's strange though, is that after that it says it shut down a few other services and then it claims to have reboot normally. It seems not to have logged that I had to give it the reboot command from the terminal a little while later. I know for sure that the reboot command that comes just before the part I posted above was from the gui, because the log says it started up again almost a minute later and a reboot doesn't take that long (at least I'm pretty sure...).

---

### Post by jordilin on 2006-07-27
> **shoofy said:**
> The only thing that caught my eye as suspicious in syslog was:

Jul 25 18:00:14 localhost shutdown[7460]: shutting down for system reboot
Jul 25 18:00:15 localhost init: Switching to runlevel: 6
Jul 25 18:00:17 localhost kernel: [66746.284000] [fglrx:firegl_rmmap] *ERROR* map 0xdfbde950 still in use (map_count=1)
Jul 25 18:00:17 localhost kernel: [66746.324000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfbde940 still mapped
Jul 25 18:00:17 localhost kernel: [66746.356000] [fglrx:firegl_rmmap] *ERROR* map 0xdfba1650 still in use (map_count=1)
Jul 25 18:00:17 localhost kernel: [66746.384000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfba1640 still mapped
Jul 25 18:00:17 localhost kernel: [66746.416000] [fglrx:firegl_rmmap] *ERROR* map 0xdfbdea50 still in use (map_count=1)
Jul 25 18:00:17 localhost kernel: [66746.448000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfbdea40 still mapped

I see that you are using the fglrx ati drivers. It's very likely that they are causing this problem. If I'm not wrong there are some issues with fglrx drivers. I would go with the generic ati ones (the ones I'm using without any problem). So, to solve these freezings, change your ati drivers.

---

### Post by 3rdalbum on 2006-07-27
The ATI drivers in the repositories for Dapper are buggy, and have been known to cause lockups when shutting down, restarting, logging out, or switching to a virtual terminal.

Try installing the latest version of the drivers from the ATI website, they fixed my problem and will probably fix yours.

---

### Post by jordilin on 2006-07-27
> **3rdalbum said:**
> The ATI drivers in the repositories for Dapper are buggy, and have been known to cause lockups when shutting down, restarting, logging out, or switching to a virtual terminal.

Try installing the latest version of the drivers from the ATI website, they fixed my problem and will probably fix yours.

3rdalbum, Is there more performance (apps loading more quickly) if you use the proprietary ati drivers from ati website than the generic ati ones?

---

### Post by shoofy on 2006-08-23
Hmm... didn't see replies to this thread until I checked it now. I think I have the ATI drivers from the website. If I don't that was a lot of time wasted trying to install them. I'll try updating/reinstalling them and see if it helps.

---

### Post by shoofy on 2006-08-23
Never mind. After fixing some intermediate problems that arose from trying to fix this, somehow it started working again. Apparently one of the things I did fixed it, but I have no idea which one. In any case, I'm glad that I can now show people how easy Ubuntu is to use without having to use a terminal command just to shutdown. It kind of kills my point.

---

### Post by davbren on 2007-10-08
Hi, I'm having the same problem with the shutdown and logoff while using Beryl. I am however using a Nvidia onbaord card...

---

