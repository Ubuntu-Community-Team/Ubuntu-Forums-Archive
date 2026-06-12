---
title: "Bash refuses to exit if ssh'ed to another machine and you run update-manager"
date: 2014-10-21
forum: General Help
---

### Post by defaria on 2014-10-21
I've experienced this for a while and it's definitely repeatable. I'm finally getting around to reporting it. If I ssh to another system then say do sudo update-manager, displaying the window back to me through ssh's X forwarding, after I exit update-manager and exit bash, bash hangs and doesn't exit. This happens every time. So:

```

$ ssh -X othersystem
othersystem:sudo update-manager
othersystem:# update system then exit update-manager
othersystem:exit
<hangs>

```

I can Control-C here and bash will exit but what causes this?

---

### Post by tgalati4 on 2014-10-21
Try the same commands with -Y and -2 switches and see if you get the same behavior.  *ssh* is pretty aggressive about session timeouts.  So when the othersystem disconnects, it locks up the local terminal.  That has been my experience.  If I use "logout" or sometimes "exit" it will cleanly exit and leave the local bash terminal intact.  The login shell has different environment variables set versus YABT--yet another bash terminal.

---

### Post by defaria on 2014-10-23
I tried it with -Y and -2 and typed exit when done. Still the same hang. Note I have a script I call update-system which does does the update without a GUI. It is essentially:

#!/bin/bash
uptrack-upgrade -y -q > /dev/null 2>&1
apt-get update  -qq   > /dev/null 2>&1
apt-get upgrade -qq   > /dev/null 2>&1

If I run this in an ssh terminal then exit it works just fine. So this is apparently an interaction with the fact that update-manager uses a GUI (Qt? Tk? I'm not sure).

---

### Post by tgalati4 on 2014-10-23
I don't understand your Use Case.  Why would you need to run update-manager if apt-get update and apt-get upgrade brings your system up to date?  Semi-automated updates can break a server because you can't see what is being updated (like the kernel), which requires a reboot, and possibly downtime if the system doesn't come up correctly with a new kernel.

Sometimes you need a desktop environment to correctly handle GUI applications.  Perhaps run *gnome-panel *and then call *update-manager* from the panel.  Then when finished, it should close cleanly.  When you run *update-manager* in a script and it finishes, it expects to be docked in a panel.  If you are not running a desktop environment with a panel, then you have a problem.

---

### Post by spjackson on 2014-10-24
> **defaria said:**
> 
I can Control-C here and bash will exit but what causes this?
I don't have a solution to this but I do observe the same behaviour (primarily when connecting to an old 10.04 server) and I believe it has something to do with dbus. (See "man dbus-launch" which makes reference to this.)

Edit:
I've added killall dbus-launch to ~/.bash_logout and that seems to be doing the job for me so far.

---

### Post by defaria on 2014-10-24
I don't **need** to do anything. I don't need to update. I'm just reporting behavior which I believe comes from some bug somewhere. 

I use ksplice so I don't need to reboot. I've been automatically updating all of my systems for years now without a single bad incident.

Well I do run gnome-panel but I can't run update-manager from the panel when I'm on another machine! Again, I'm sshing into another, remote machine. At that point I'm at a bash shell and there is no GUI because it's on a different machine. Running update-manager and displaying it's window remotely back to my desktop using ssh's X11 forwarding seems to be the key to the problem. No other gui run remotely and displayed back through X11 forwarding hangs when I exit. And there is no reason why update-manager should do this nor require a gnome-panel, which is why I'm reporting this. There's no problem with running update-manager using ssh and forwarding the GUI down the X11 forwarding **except** that it hangs when you log out. You can run update-manager, exit it, do a bunch of other things both CLI and GUI but since you ran update-manager once you will be stopped when you log out. That's incorrect behavior as no other app does that. Hell you can run synaptic and use that to update your system then log out and you''l not be stopped. update-manager just has a bug.

---

### Post by tgalati4 on 2014-10-24
But only update manager puts notifications in your panel--like "Need to Reboot" or "Repositories failed to Update", so I think the lack of a panel means you have a hung process since the notification has no place to land.  I can run gnome-panel over an existing panel.  It's confusing as heck, but it can be done.  You have to be clever with the mouse and put autohide on so the panels will rise and fall at different rates.  The remote panels are slower to rise and fall.  I don't think it is a bug.  It is a behavior related to a Use Case that update-manager was not programmed for.

If I try to run update-manager in KDE, I would expect some weirdness.

---

### Post by defaria on 2014-10-25
Interesting. One would think that to put a notification in the panel would mean it just does some IPC stuff to tell the panel "Hey I have a message for the user. Put this in your alert system" and it would be finished. But here I'm running ssh and displaying back. So mars (my laptop) would be displaying the update-manager window back to earth (my desktop) and when update-manager exits it's trying to tell gnome-panel running on earth about events that only make sense for mars. It probably does this through the dbus mechanism as spjackson seems to have figured out. And there's probably some security thing why you don't want strange machines talking to your DBUS.

What I can't figure out though is why doesn't the IPC message sent timeout after some time. That seems like the solution to this dilemma.

---

