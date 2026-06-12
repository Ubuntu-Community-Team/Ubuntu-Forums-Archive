---
title: "Strange behaviour with Ubuntu 16.04 on DELL XPS 9550 - freezing, slowing down, etc"
date: 2016-05-21
forum: General Help
---

### Post by Nikolay_Andronov on 2016-05-21
I am experiencing some issues recently with my Dell 9550, core i7, 512 SDD, nVidia 960GTX, non touch.
The machine is slowing down regularly, I need to reboot it in order to get some performance out of it. Sometimes it freezes for no obvious reason, it just hangs and only hard reboot helps. The newest thing however, is that it shuts down after lid is closed, although nothing is wrong with the settings. It even plays ubuntu welcome sound on closed lid, happened just now. 
Few days ago, by accident, I ran ```
find . -type f -exec chmod 644 {} \;
``` while I was in my /home directory, instead of the one I was supposed to run that command from, but I realized what I did in the moment I hit enter, so I aborted in less than a second with Ctrl+C. Anyway, the problems were persistent beforehand, so even if that made some damage, it is not related.
Any help will be highly appreciated, just tell me what outputs I need to provide for more information.

PS: Forgot to mention, that after the last reboot after suspend, the touchpad wasn't working, so I rebooted again. Also, although probably not related, but alt+ctrl+f* doesn't work, I need to press alt+ctrl+fn+f* and when I want to go back to graphic interface, nothing happens after alt+ctrl+fn+f6, so I'm rebooting again. :(
PS2: Every now and then, my wi-fi disappears, and strangely, rebooting won't help but ```
sudo service network-manager restart
``` will do the job.

---

### Post by vanadium on 2016-05-23
Your find chmod command should not have created too much havoc, i.e., it would be restricted to your user folders. To test if that might be the issue nevertheless, you could create a new account and see whether the issues persist when logged in there.

Check also the output of dmesg, the kernel messages. You can have "live updates" with the command "dmesg -wH". Notice in particular messages in red. I have a new Dell XPS 9350. It would freeze randomly (after 2 minutes, after 10 minutes, after 1h30). I spotted "mce: [Hardware Error]: Machine check events logged" errors now and then in dmesg. They got the mother board replaced and that fixed the problem.

---

### Post by morhook on 2016-06-13
Just checked going to alt+ctrl+fn+f* works ok as you have said. To come back I pressed alt+ctrl+f7 (notice that is WITHOUT fn). For restarting the wifi I do same command round here (using stock kernel and drivers from Ubuntu 16.04)

---

