---
title: "upgrade 16.04 to 18.04 - Terminal won't open"
date: 2021-08-21
forum: General Help
---

### Post by tjrob137 on 2021-08-21
I just upgraded by VMware VM from Ubuntu 16.04 to 18.04.5. The Terminal won't open, it just displays spinning dots in a circle for ~ 20 seconds.
This makes it useless to me. Any suggestions? -- there is a thread that suggests using a Terminal command, which is obviously useless.

Or do I need to try again,  installing 18.04 from scratch?

---

### Post by grahammechanical on 2021-08-21
My advice would be to re-install Gnome terminal. But how can you do that if you cannot open a terminal? Open Ubuntu Software. Search for Gnome terminal. Click in the Gnome terminal section and in the window that opens click on Remove. Having done that click on install.

There is a way to run commands without having the desktop and user interface loaded. At the Grub boot menu select Advanced Options for Ubuntu. Then select a Linux kernel with recovery mode. At the Recovery menu select Network to set up an internet connection. When back at the recovery menu select Root. That will give a root shell where commands can be run. To leave the root shell type exit. When back at the Recovery menu select Resume to continue the boot process.

Regards

---

### Post by monkeybrain20122 on 2021-08-21
So it appears when you "upgraded" the old python3 symlinks are broken. [https://stackoverflow.com/questions/61144232/updated-to-python-3-8-terminal-wont-open-fixed-but-details-not-understood](https://stackoverflow.com/questions/61144232/updated-to-python-3-8-terminal-wont-open-fixed-but-details-not-understood)
This is an example why you should always do clean install instead of "upgrade".

---

### Post by tjrob137 on 2021-08-22
I found that both xterm and uxterm work fine. Crisis averted.

The python3 symlinks are fine: /usr/bin/gnome-terminal starts with #!/usr/bin/python3, and typing that command into xterm runs python 3.6.9 just fine.

Running gnome-terminal from xterm just hangs for a long time, then:
> # Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory): Error calling StartServiceByName for org.gnome.Terminal: Timeout
I have no idea what that means or how to fix it.

I tried this:
> sudo apt-get remove gnome-terminal
sudp apt-get install gnome-terminal
It removed then restored the terminal icon on the left, but it behaves the same and doesn't work; same error message in xterm.

I tried this:
> sudo apt-get update
sudo apt-get upgrade
but it upgraded nothing and did not fix gnome-terminal.

So I put xterm into favorites and will be using it.

---

### Post by monkeybrain20122 on 2021-08-22
[https://askubuntu.com/questions/608330/problem-with-gnome-terminal-on-gnome-3-12-2](https://askubuntu.com/questions/608330/problem-with-gnome-terminal-on-gnome-3-12-2)

---

### Post by tjrob137 on 2021-08-22
None of the suggestions in the linked threads worked. 

I'm giving up on gnome-terminal and using xterm.

---

