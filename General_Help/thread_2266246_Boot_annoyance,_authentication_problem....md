---
title: "Boot annoyance, authentication problem..."
date: 2015-02-21
forum: General Help
---

### Post by timgood on 2015-02-21
I posted here a week or so ago and thought I had solved my problem. However, on rebooting, the annoyance has come back. This is my sad story:

I'm running Kubuntu 14.10 64bit. Following some updates about two weeks ago I'm getting some weird behaviour. Sometimes when I boot, the desktop loads normally but some applications (shutter, kup, conky) do not load. When I try to launch systemsettings and some other applications, I get a message saying 'kdeinit could not launch...' and the reboot, shutdown and logoff buttons become unresponsive. I can also not update the system using muon (it says authentication was not given, although it is not asked for.) I can update, install  and launch applications directly from the terminal without any problems.

If I force a logout using 'sudo service lightdm restart' I just get a black screen. I can launch a terminal from there by hitting F1. After logging in, I can 'startx' and all my system tray icons for shutter, kup etc. come back and the desktop behaves normally. Then I reboot and the desktop launches fine. But subsequent reboots make the problem start again. 

I suspect that it is something to do with PAM but this is driving me mad. Any ideas or suggestions as to what could be causing this and what I could do to fix it? I've tried 'sudo pam-auth-update --force' and other fixes, but the problem persists.

---

### Post by timgood on 2015-02-22
My thanks to Qqmike from Kubuntu forums for this suggestion: boot into a terminal and delete .Xauthority, then reboot. 

> Quoted from my recent thread:

You don't need to boot into recovery mode to remove .Xauthority. You can remove it from normal boot:

1. [when the login screen is visible] -- or when you can get a terminal, press Ctrl+Alt+F1 (to change to a virtual text terminal) 
2. login with your user credentials
3. run 'rm ~/.Xauthority'
4. logout from terminal ( "exit" or Ctrl+d)
5. Switch back to the login screen (Ctrl+Alt+F7)

This seems to have fixed the problem - I will monitor and if it stays this way, will mark this as solved. Again!

---

