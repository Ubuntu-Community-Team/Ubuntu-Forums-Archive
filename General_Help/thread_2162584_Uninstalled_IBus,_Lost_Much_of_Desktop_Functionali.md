---
title: "Uninstalled IBus, Lost Much of Desktop Functionality -- How to Restore?"
date: 2013-07-15
forum: General Help
---

### Post by Ubuntist on 2013-07-15
A few minutes ago I uninstalled everything related to IBus that I could find in Synaptic, because I was having trouble getting IBus to allow input of Chinese characters and wanted to re-install it from scratch.

Well, that seems to have been a big mistake, as I've completely lost the launcher bar and the system bar (or whatever you call the bar at the top of the screen).

I got to a command prompt (by clicking on a document and then hitting Alt-F4 [clicking the close button didn't work] -- the desktop disappeared and I was left with a prompt).  I then tried
```

sudo apt-get install ibus

```
That seemed to run OK, but my there is still no launcher and no system bar (I'm typing all of this on a back-up machine).

I'm really at a loss for what to do next; I'd really rather not re-install 13.04 from scratch.

Could anybody give me a hint as to how to make the system usable again?

Thanks much!

---

### Post by dino99 on 2013-07-15
reinstall the metapackage: 
sudo apt-get install --reinstall ubuntu-desktop  (for gnome DE; adapt for other DE indeed)
sudo dpkg-reconfigure -phigh -a  (can take a while, be patient)

and of course, think to clean/autoclean/autoremove/gtkorphan/bleachbit your system

if you are logged with unity (aka ubuntu), then reset both compiz/unity:
dconf reset -f /org/compiz/
setsid unity

then logout/in

---

### Post by Ubuntist on 2013-07-15
Thanks very much, dino99.

I've tried the steps you suggest, but my Unity desktop remains as before.  Here's what happens....

I  boot up and get to the Unity desktop.  Then I hit Alt-F4 and get a  command-line login prompt (if the launcher were working, I would just  open the command line directly, without having to log in again).  Then I  log in.

Then I run the "apt-get install" and "dpkg-reconfigure"  commands that you give.  The first seems to run fine, but the second  terminates with about a dozen lines like```

/var/lib/dpkg/infocompiz.config: 1: /var/lib/dpkg/info/compiz.config: [general] not found

```

Then I try the dconf command, being careful to include the final `/'.  It returns with```

error:  Error spawning command line `dubs-launch --autoluanch=a....  --binary-syntax --closestderr': Child process exited with code 1
```

Then I run the `setsid unity' and get a few more complaints, beginning with
```

WARNING: no DISPLAY variable set, setting it to :0

```

I  have the feeling things would work better if I executed the commands  within the same shell that's running unity, rather than after logging  into a separate no-graphical shell.  Without the launcher bar, though, I don't know how to get to a command-line without hitting Alt-F4 and logging in again.

Any ideas?

---

### Post by Ubuntist on 2013-07-17
I got some help from plucky and sudodus in another thread and was able to open a command-line window with Ctrl Alt t.  Then, following the instructions provided by dino99 got my system back on its feet.

Problem solved!

THANKS A LOT!!!

---

