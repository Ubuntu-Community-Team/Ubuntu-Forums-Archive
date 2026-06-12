---
title: "Login screen keeps returning"
date: 2014-02-15
forum: General Help
---

### Post by stepheny on 2014-02-15
I was logging onto a remote machine via ssh and then starting lxde on the remote machine. Everything worked fine and so I tried using VNC. Again no problems. I then thought that if I started a new Xsession on my main machine maybe I could forward the Xsession from the remote machine to the mail one without VNC. So on the main machine I typed something like:

startx -- :1

A new session started but I couldn't get a terminal or close the session. I tried CTR-ALT-F7 and CTR-ALT-F8 but nothing happened. Eventually I rebooted the computer. Now Ubuntu loads and I get to the login screen but after entering my password the screen goes blank and then returns to the login screen. I cannot get to my desktop, even though I do not get a warning that the password is wrong as I do it I enter a bad password. I have logged on as guest to write this plea for help. As Guest if I go to System Setting/User Accounts I can see that my password is still good but if I set to Automatic Login I still get the same problem after restarting.

Does anyone know how I can fix this?

---

### Post by stepheny on 2014-02-15
It seems that .Xauthority got corrupted. I fixed the problem by logging on as guest and opening a shell with Ctrl-Alt-F1 and logging on as the user. Then:

```
cd /home/user
sudo mv .Xauthority .XauthorityBak
sudo reboot
```

Everthing is back to normal now.

---

