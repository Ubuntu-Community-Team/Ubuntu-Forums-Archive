---
title: "Hard disk led simulator on screen"
date: 2019-11-08
forum: General Help
---

### Post by Gingalone on 2019-11-08
I have a Dell XPS laptop (Ubuntu 18.04) which doesn't have a HD activity led on it. I saw on the web there are some on-screen HD led simulator for Windows: is there something of the like for Linux/Ubuntu?
Just a simple little flashing light somewhere on screen... I really would like that! 
Thank you for suggestions.

---

### Post by jetsam on 2019-11-10
Possibly give conky a try:
[How To Install and Use Conky in Ubuntu Linux]("https://itsfoss.com/conky-gui-ubuntu-1304/")

You could probably make a very minimal setup that just showed a "hard drive active" display of some sort, but I'd explore the options with a basic install first so you can learn the system and see what it can do.

---

### Post by HermanAB on 2019-11-10
See 'gkrellm'.

---

### Post by oldrocker99 on 2019-11-10
Ubuntu MATE's System Monitor has a HD activity indicator available, and, for that matter, CapsLock and NumLock.

No HD LED shows the difference between read and write operations. I set it to red for read, and white for write, and have a better idea of what's going on when the HD light comes on.

---

### Post by Redalien0304 on 2019-11-10
[COLOR=#000000]Ubuntu MATE's System Monitor has a HD activity indicator available, and, for that matter, CapsLock and NumLock.[/COLOR]
Can that be installed in the Cinnamon DE?

---

### Post by Gingalone on 2019-11-11
Thanks a lot for suggestions; then I installed the package mate-system-monitor_1.20.2-1_amd64.deb and tried it:
```

:~$ mate-system-monitor

** (mate-system-monitor:23355): WARNING **: 14:39:56.203: SELinux was found but is not enabled.

I/O warning : failed to load external entity "/usr/share/mate-about/mate-version.xml"

```
and then I get a window of the classic normal System Monitor (no HD monitor option)
What about?

---

