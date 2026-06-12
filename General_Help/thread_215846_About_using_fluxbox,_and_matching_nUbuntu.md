---
title: "About using fluxbox, and matching nUbuntu"
date: 2006-07-14
forum: General Help
---

### Post by roostishaw on 2006-07-14
Hello,
How can I get my own installation of Fluxbox (using sudo apt-get install fluxbox) to look exactly (if possible) like the desktop of the live cd version of nUbuntu?
You can find some screenshots of what I'm looking for [here]("http://www.nubuntu.com/screenshots.php").

1) Which config files, if any, do I copy, and to where?
2) What theme is that using? (will it be included if I move some config files?)
3) Is there an equivalent to the 'taskbar' in Fluxbox?
4) How do I add programs (like gaim, firestarter, and network manager) to startup?
5) Will Network manager work the same as in gnome?

Thanks for reading. If you know the answers to any of those questions, please enlighten me.
~roostishaw

---

### Post by roostishaw on 2006-07-14
Well, I just booted from the live cd again. In the /home/nubuntu/ directory I see folders like: .fluxbox, .themes, and so on. Are these the folders that hold the config files for fluxbox?
If so, how do I copy them to my hard drive? (or wherever they need to be to take effect in fluxbox)

Thanks!

---

### Post by DJ Scribblinni on 2006-07-15
I've never heard of nUbuntu, I will be trying this out.  You are correct, anything that is in that .fluxbox folder contains all the styles and the configuration of the desktop.  Simply just copy that folder to your hard drive.  There is a taskbar in Fluxbox, just open any program that puts something there, such as gaim, and you'll see the default position, which is right next to the clock.

The programs you said you want to add for startup, theres a file ./fluxbox/startup

Just place what you want to startup simply as
```
gaim &
firestarter &
#if you use the startup file as the way to start fluxbox
#be sure to put this next line last!
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
```
the & keeps them running once they start. 

Here's a couple of sites that you may want to take a gander at; all about fluxbox:
[http://www.linuxmanpages.com/man1/fluxbox.1.php]("http://www.linuxmanpages.com/man1/fluxbox.1.php")
[http://fluxbox.org/docs/en/faq.php]("http://fluxbox.org/docs/en/faq.php")
[http://fluxbox.org/docbook/en/html/]("http://fluxbox.org/docbook/en/html/")
[http://www.ubuntuforums.org/showthread.php?t=116759&highlight=xinerama]("http://www.ubuntuforums.org/showthread.php?t=116759&highlight=xinerama")

---

### Post by roostishaw on 2006-07-16
Thanks for the reply.
I only have a few more issues with fluxbox, then I'll be all moved in.

1) I use NetworkManager to connect to my WPA enabled wifi network. The trouble is that I have it set to launch on startup ('nm-applet &' in the ~.fluxbox/startup file). It seems to "go" just fine (has its icon in the taskbar and all), but the problem comes when it tries to connect. It will ask for the WPA password for the network, and not the password for the gnome-keyring, like in gnome. After I provide the network password, it connects, but the internet dosn't work... The internet begins to work only after I log into gnome, give it my keyring password, then log back into fluxbox.

2) I can't seem to get my shortcut keys to work. I want it so that I can just press the right windows key, and that will launch gnome-terminal.

3) I already modified the sudoers file so that I could run firestarter as root without giving the password. In ~.fluxbox/startup I have 'gksudo firestarter --start-hidden'. Nothing happens... no icon in the taskbar or anything. Also tried just 'gksudo firestarter'. Same result...
EDIT: I put 'xhost +' followed by 'gksu -g /usr/sbin/firestarter' in the startup file. **But it still dosn't start minimized...**

4) Lastly (not really a need, but it bugs me...), when gaim launches on startup, its icon has a white background... and not the black-ish color as my taskbar.

I'm still googling, but if you know the solution for any of those, it would be appreciated.
Thanks!

---

### Post by DJ Scribblinni on 2006-07-16
Your first question, I can't help ya with.

For the second question, fluxbox is a different window manager, and therefore uses different key shortcuts.  Heres a link on how to modify the keys file
[http://fluxbox.sourceforge.net/docs/en/newdoc.keybindings.php]("http://fluxbox.sourceforge.net/docs/en/newdoc.keybindings.php")

Your third question, I don't use firestarter, and the shortcut you said you tried, I would've thought would work...

And the gaim taskbar icon, I have the same issue, I think its the icon coloring itself.

---

### Post by roostishaw on 2006-07-16
Adding
```

Mod4 :Exec gnome-terminal

```
...to ~.fluxbox/keys has no effect.

Anyone?

---

### Post by DJ Scribblinni on 2006-07-16
You know, the only keybindings seem not to work very well for me, but then again I also use the 1.0rc2 version of fluxbox.  I believe it should be ```
Mod4 :ExecCommand gnome-terminal
```  But then again that doesn't even work for me.

---

### Post by roostishaw on 2006-07-17
Got it:
```

Super_R :ExecCommand gnome-terminal

```

Anyone know about the Network manager issue? Do I have to start another process along with Network Manager like the gnome-keyring?
And for the question about gaim, which icon is the one in the taskbar (so I can just modify that one)?

---

