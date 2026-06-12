---
title: "Gui remote install"
date: 2018-12-04
forum: General Help
---

### Post by urtihu on 2018-12-04
Hi all

I was googling for a while, but I only find how create a remote GUI access on a system where I have physical access to. I have a virtual minimal install in the cloud with putty access and I would like to use it as a LINUX workstation. How would I proceed to install a GUI and a GUI access to it from a windows or LINUX client from a minimal install having only putty as an access in the beginning.

---

### Post by HermanAB on 2018-12-04
Well, basically, it is not done that way on UNIX systems.

What you should do instead, is run an X-server on your local system (not Wayland).  Then, you run an application remotely, while rendering it transparently on the local desktop using SSH:
$ ssh -X user@server "gedit filename"

Gedit will then pop up on the local desktop.

There is no point in sending a whole desktop over the wire in order to overwrite a perfectly fine local desktop.  Since your local machine already has everything, you only need to remote the application.

Remoting the whole kit and kaboodle, wasting tons of bandwidth and making everything slow in the process, is the Windows way.

Another advantage of remoting only the applications, is that you can do the same with multiple remote machines at the same time and click drag drop files from one machine to the other etc.  It is much more powerful than remoting a single machine desktop.

---

### Post by urtihu on 2018-12-05
@HermanAB: I found a solution for what I proposed, but your method makes much more sense. Your arguments are excellent. I will reinstall it and use yours. Thank you very much.

---

