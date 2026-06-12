---
title: "firejail / Xephyr suddenly not working properly for secure firefox environment"
date: 2021-05-01
forum: General Help
---

### Post by Peter_Brandon on 2021-05-01
I was quite pleased to discover that I could create a reasonably secure 'desktop' environment for Firefox using firejail with xephyr and fluxbox.  Had been using VirtualBox, but it takes to much memory and CPU.

My firejail environment was working perfectly, but after a reboot and after some updates it suddenly has serious problems, and I have no idea how to fix it.

I created the firejail environment with (in practice, I use more complex security switches, but the following reproduces the problem):

```

firejail --x11=xephyr --xephyr-screen=1920x1080 fluxbox &
#get the display number:
firemon--x11
#Attach firefox / mousepad:
DISPLAY=:390 firejail firefox &
DISPLAY=:390 firejail mousepad &

```

This *was* working perfectly, but after a reboot about a week ago it started doing the following:

Firefox opens as a window in the upper left of xephyr.  The window cannot be moved or resized (and it's too small).

When mousepad is open, anything I type or paste in a Firefox text box gets typed or pasted into mousepad instead.  This means I cannot copy or paste anything (passwords, URLs, etc.) from mousepad into Firefox.  When I close mousepad, text that I had copied from mousepad disappears from the clipboard, so it still cannot be transferred to Firefox.

I've tried to purge-remove and then reinstall: firefox, mousepad, xephyr, and fluxbox.  I also deleted all firefox cache / config files.  But the problem behaviors persist.

Any thoughts on what else I might try or what might be wrong?

---

### Post by &amp;KyT$0P# on 2021-05-01
Can you please post the output of the following commands run in Terminal? -
```
lsb_release -a
uname -r
firejail --version
apt-cache policy firejail
```

Have you tried opening Terminal windows directly from the fluxbox in your firejail Xephyr, then from those Terminals running Firefox/Mousepad/whatever?

---

### Post by Peter_Brandon on 2021-05-01
Oh, and to make this even weirder:  While the firefox window is fixed position, un-resizable, and has no close / minimize buttons, the mousepad window is changeable position, resizable, and has close / minimize buttons.

---

### Post by Peter_Brandon on 2021-05-01
Thanks halogen2!

Good idea to try running firefox & mousepad from within xephyr.  Unfortunately, I run into the same problems.

Here is the info you requested (see below).  Interestingly, I was able to copy / paste using the right mouse button.

> [FONT=monospace]
[COLOR=#000000]$ lsb_release -a [/COLOR]
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 20.04.2 LTS 
Release:        20.04 
Codename:       focal 
[COLOR=#000000]$ uname -r [/COLOR]
5.8.0-50-generic 
[COLOR=#000000]$ firejail --version [/COLOR]
firejail version 0.9.62 
[COLOR=#000000]$ apt-cache policy firejail [/COLOR]
firejail: 
  Installed: 0.9.62-3 
  Candidate: 0.9.62-3 
  Version table: 
 *** 0.9.62-3 100 
        100 /var/lib/dpkg/status
[/FONT]

---

### Post by &amp;KyT$0P# on 2021-05-01
Did you disable the universe section of the standard Ubuntu repositories?

Are you using custom firejail profiles?
Can you please post the output of each individual firejail command you're running?

Have you tried renaming your [FONT=Courier New]~/.fluxbox[/FONT] directory to start from a clean Fluxbox configuration?

---

### Post by Peter_Brandon on 2021-05-01
Hi halogen2:

My Ubuntu repositories include universe, and I am using the standard firejail profiles that were downloaded with firejail by synaptic.

Good idea to try to rename .fluxbox directory so I'd get a clean configuration.  Unfortunately, this had no effect--am still getting those problems.

I'm enclosing a copy of what I get when I open fluxbox, firefox, and mousepad using firejail.  I think it wasn't able to connect to ibus before these problems occurred as well as currently.

Thanks for your thoughts!

---

### Post by Peter_Brandon on 2021-05-02
I just tried openbox and it is working without the issues I'm experiencing in fluxbox.  I prefer fluxbox, but not with those issues.  Seems the simple solution for me is to switch to openbox, though I wish I could figure out why it suddenly started having these issues.  

Thanks again halogen2 for working on this with me!

---

