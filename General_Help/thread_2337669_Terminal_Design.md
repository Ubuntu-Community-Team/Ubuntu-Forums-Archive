---
title: "Terminal Design"
date: 2016-09-20
forum: General Help
---

### Post by lesl.ie on 2016-09-20
This seemed to be the most fitting section for this question, atleast from the threads I saw.
Anyways.

Lately I've seen a lot of people have terminals with like 2 lines, the top one being the PS1 prompt and the other displaying things such as time and directory, but it was in the bottom of the terminal window.

Here's an example [http://img.wonderhowto.com/img/52/07/63562590172234/0/customize-your-kali-linux-desktop-and-transparent-terminal.w654.jpg](http://img.wonderhowto.com/img/52/07/63562590172234/0/customize-your-kali-linux-desktop-and-transparent-terminal.w654.jpg)

---

### Post by howefield on 2016-09-20
Thread moved to the "*General Help*" forum.

Looks like an application called tmux.
> 
Description-en_GB: terminal multiplexer tmux enables a number of terminals (or windows) to be accessed and controlled from a single terminal like screen. tmux runs as a server-client system. A server is created automatically when necessary and holds a number of sessions, each of which may have a number of windows linked to it. Any number of clients may connect to a session, or the server may be controlled by issuing commands with tmux. Communication takes place through a socket, by default placed in /tmp. Moreover tmux provides a consistent and well-documented command interface, with the same syntax whether used interactively, as a key binding, or from the shell. It offers a choice of vim or Emacs key layouts.

---

### Post by dragonfly41 on 2016-09-20
Yakuake (in Ubuntu repo) is another useful tool which allows multiple shells.
Toggle show/hide dropdown terminal with F11.

---

### Post by lesl.ie on 2016-09-20
If I use Tmux, how can I customize it to change how it looks?

---

### Post by QIII on 2016-09-20
yakuake is liable to pull in a lot of KDE dependencies that may be unwanted.  I use KDE and yakuake myself, but I'm not sure I'd be in a rush to use it without KDE.

Terminator may be a better choice.

---

### Post by howefield on 2016-09-20
> **lesl.ie said:**
> If I use Tmux, how can I customize it to change how it looks?

To install :
```
sudo apt-get install tmux
```

Then open a terminal and type tmux to start....

Manual Page : 
```
man tmux
```

First I'd do is change the modifier key from Ctrl + b to something more user friendly to a single hand :)

---

### Post by lesl.ie on 2016-09-20
Thanks :)

---

