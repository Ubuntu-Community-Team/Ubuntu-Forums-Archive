---
title: "Can't login after accidental suspend (encrupted home)"
date: 2014-12-26
forum: General Help
---

### Post by rwigle on 2014-12-26
I accidentally hit the suspend button on my Toshiba Tecra R700 (Ubuntu 14.04) at the end of the day. [More haste, less speed]. Now I can't login. The home folder has been encrypted for several months now.

When I boot, I get the login screen and enter the password. Ubuntu seems to be loading, but then (after 5--6 seconds) gives me the bongo sound and a new login screen. Note: It does not complain about the password being wrong. [If I enter an incorrect password it does complain.]

I have looked at other posts, but don't see anything quite the same. My valuable data files are all on a cloud server, if that matters.

Question: This may be a red herring, but I knew (thought) that suspend was broken with encrypted home. If so, why is it so easy to do by accident?

Thanks in advance everyone.

---

### Post by schragge on 2014-12-26
Try to change to a virtual console with Ctrl+Alt+F2, and login in text mode from there. This way you won't miss any error messages if something goes wrong.

---

### Post by rwigle on 2014-12-28
That was a great suggestion. The command-line login worked (no errors visible). I was also able to see all my data files. Just one problem. I still have exactly the same behaviour when I try to log in via Unity. I keep getting dumped back to the login screen with no error.

Does the system try to `recover' from the suspend when logging in via Unity/Gnome, but not when logging in via text/command-line?

---

### Post by schragge on 2014-12-28
Ok, nice to hear you've got it to the command prompt. A very common problem is the wrong ownership of ~/.Xauthority and/or ~/.ICEauthority files.
While logged in from the console, do
```

sudo chown $USER: ~/.{X,ICE}authority

```
then change to the GUI login screen with Ctl+Alt+F7 and try to log in there.

---

### Post by rwigle on 2014-12-28
Thanks for the quick response. Regrettably, the same login behaviour. Will reboot and check that I have ownership of those files fixed.

Edit: Ownership seems right they are noth -rw------ and owned by me.

---

### Post by rwigle on 2014-12-28
After reboot, I thought I was making progress, because before the login prompt came up I got the message saying (something like) "encrypted drive not mounted or missing, wait, ???, ???".

Unfortunately, when I enter my password I just get dumped back to the login screen. (Again, no "wrong p/w" message.)

---

### Post by schragge on 2014-12-28
Ok. pastebinit should be installed on you system. So you'll be able to run
```
pastebinit -i ~/.xsession-errors -i /var/log/Xorg.0.log
```
and provide the link to paste.ubuntu.com with the results. Let's see if we can find any hints there.

---

### Post by schragge on 2014-12-28
Also, have a look at [this answer]("http://askubuntu.com/questions/341979"). Is that the message you've got on login?

---

### Post by rwigle on 2014-12-28
pastebinit needed to be installed (Way cool!)

[http://paste.ubuntu.com/9635864/](http://paste.ubuntu.com/9635864/)
[http://paste.ubuntu.com/9635865/](http://paste.ubuntu.com/9635865/)

---

### Post by schragge on 2014-12-28
Ok. Concerning .xsession-errors, try the first answer from [here]("http://askubuntu.com/questions/360725/") (Also, see LP #[lpbug]1184878[/lpbug]). The only strange thing I see in Xorg.0.log is what described at LP #[lpbug]954426[/lpbug]. So let's try the suggestion from there, too:
```
sudo rm -f /var/lib/xkb/*
```

---

### Post by rwigle on 2014-12-28
Thanks schragge, I was also looking at things you pointed me to and realized I had messed with PATH in /etc/environment.

I fixed that and we are away to the races.

the default path should be PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"

---

