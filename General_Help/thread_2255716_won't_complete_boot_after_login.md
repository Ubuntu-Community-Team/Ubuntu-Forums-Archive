---
title: "won't complete boot after login"
date: 2014-12-07
forum: General Help
---

### Post by JamButty on 2014-12-07
Perplexed. With no changes I can account for (e.g. new kernel or similar) my Ubuntu 14.04 system suddenly will not complete my normal login. It accepts the password (validiating correctly as wrong one will return to login prompt as it should), then just hangs. I have tried booting from several older kernels, tried the diagnostics (fsck, repair dpkg etc. but nothing gets me through. It will allow me to login as guest. safe graphic mode just hangs too.
The only lead I have is that compiz crashed by itself a couple of weeks ago, and I thought I saw compiz being rebuilt when I ran the "repair packages" option.
Any suggestions?

thanks.

---

### Post by nerdtron on 2014-12-07
Try:
On the login screen, press Ctrl+Alt+F1. You'll be dropped to a console screen. Login using your credentials. Then run "startx" to run the GUI.

---

### Post by JamButty on 2014-12-07
It does not accept my password that way. From the normal gui  it appears to accept it (screen goes blank, does not return login field) but via the console it just does not accept it as correct. It definitely has not been changed (nobody else touches this machine). I might mess up the pw once, not 6 times with reboots.
If I have to, I am willing to wipe and reload, but I do not see how to backup recent files in this situation. Neither from guest account nor a CD/stick boot do I have access to my files.

---

### Post by nerdtron on 2014-12-07
> Neither from guest account nor a CD/stick boot do I have access to my files.

password is not accepted? hhmmm

Anyway this is a different story. how come you don't have access to your files in the Live environment? Any errors? Yu should be able to copy your files.

---

### Post by JamButty on 2014-12-08
Files are accessble from CD boot environment. Tried for a long time four years ago in this regard without success, but things have changed.
figured out my account login name is different to that displayed on the login page. Once logged in, though, startx brings me to the same place (presumably trying to load unity and other start programs) and hangs.
followed a few blind alleys -  ccsm does not work so great in line mode (X11 display mode required??) - dconf solution also was outdated or just wrong - unity -reset has been deprecated and its presumable sucessor setsid unity hangs also. Giving up on fixing. Will wipe and reload. thanks.

---

