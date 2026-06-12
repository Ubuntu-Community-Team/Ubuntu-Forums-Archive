---
title: "Fluxubuntu post installation command line?"
date: 2007-11-19
forum: General Help
---

### Post by Grafster on 2007-11-19
Was having Xorg related Xubuntu problems; couldn't seem to get it fixed. --> Clean install. 

Didn't really love Xfce (I guess I underestimated how much of ubuntu is Gnome?) anyway I decided to just move to fluxubuntu.

Installed successfully but it just dropped me to a login. Is that normal behavior? What's the command line to launch fluxbox?

[The forums, etc. don't seem to mention this behavior post install, so I have a creeping suspicion that, since it looked like the Fluxubuntu install process was apt-getting xorg instead of installing it from the CD that it's picked up the same xorg/kernel combination that kept Xubuntu from working. Prove me wrong! I would love to be wrong!]

---

### Post by taurus on 2007-11-19
What happens if you run this command from a prompt?

```
startx
```

---

### Post by Grafster on 2007-11-20
OK. I thought there might have been some sort of fluxbox graphics manager/command line.

When I try to start x the same Xorg message that's been bugging me since the kernel update this weekend.

Either
1: Screen(s) found but none have a usable configuration. I've been putting different, really simple, screen configurations in for days. I put in the screen resolutions for the computer listed on the manufacturer website; variations on that. Litterally nothing works.
OR
2: The screen goes blank. Like it's off. (I'm assuming that Xorg thinks its working and is happily thinking it's showing me the gui). But I see nothing.

---

### Post by Grafster on 2007-11-20
In the second case I can "see" the fluxbuntu shutdown screen for a second when I hit the shutdown button. So it's not hung, or crashed, or whatever.

---

