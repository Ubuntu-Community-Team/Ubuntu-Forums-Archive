---
title: "Ubuntu 16.04: Where are the Snappy Packages?"
date: 2016-04-25
forum: General Help
---

### Post by jamesfbays on 2016-04-25
I've been reading about Snap / Snappy Packages. Sounds like a great idea. But I haven't found any. Where are they, and how can I install them?

---

### Post by jamesfbays on 2016-04-25
I've been reading about Snap / Snappy Packages. But where are they? How can I download and install a Snap Package?

---

### Post by cariboo on 2016-04-25
Make sure you have snapd install, then use the following comand to see what is available:

```
snap find
```

Running yakkety I see the following list:

```
snap find
Name                   Version                  Summary
audovia                3.2.1                    Database application for making music using JFugue MusicStrings
canonical-dragon       0.7.1                    The gadget snap for the dragonboard
canonical-i386         3.1                      The gadget snap for generic i386 systems
canonical-pc           3.1                      AMD64 generic package
canonical-pc-linux     4.4.0-18+20160419.13-26  The ubuntu-core kernel snap
canonical-pi2          3.2                      Raspberry Pi 2 support package
go-example-webserver   16.04-4                  Minimal Golang webserver for snappy
hello-world            6.0                      Hello world example
http                   4.6692016                HTTPie in a snap
links                  2.12-1                   Web browser running in text mode
moon-buggy             1.0.51.9                 Drive a car across the moon
nmap                   7.12SVN-0.4              Nmap ("Network Mapper") is a free and open source utility for network discovery and security auditing
notes                  0.0.8~snap3.gita80fd1c   Note-taking application, write down your thoughts
shout                  0.53.0                   A self hosted web IRC client
sshtron                1.0                      multiplayer Tron via ssh
tmux                   2.3bump1                 tmux
tor-middle-relay       0.2.7.6-6                Essential infrastructure node for Tor network
ubuntu-calculator-app  2.1+snap3                Ubuntu Calculator application for the Unity 7 desktop
ubuntu-clock-app       3.6+snap3                Ubuntu Clock application for the Unity 7 desktop
ubuntu-core            16.04+20160419.20-55     The ubuntu-core OS snap
xkcd-webserver         16.04-5                  Show random XKCD compic via a build-in webserver
yacas                  1.4.2                    Yet Another Computer Algebra System
```

---

### Post by cariboo on 2016-04-25
Merged duplicate threads.

---

