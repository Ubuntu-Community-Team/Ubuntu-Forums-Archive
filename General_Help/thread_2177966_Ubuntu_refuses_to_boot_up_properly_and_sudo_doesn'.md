---
title: "Ubuntu refuses to boot up properly and sudo doesn't work"
date: 2013-10-01
forum: General Help
---

### Post by arnold_layne2 on 2013-10-01
[COLOR=#000000][FONT=Arial]Ubuntu 13.04 64bit[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So this all started when I was installing laptop-mode-tool, in the middle of which Ubuntu crashed (I don't remember whether it crashed to the command line or simply crashed). Then I tried to boot it, it kept getting stuck at the loading screen. After a few tries, I CTRL-ALT-F7'd, then I saw a mouse pointer on a blank screen. Then I ALT-PRNTSCRN-K'd and then I got my desktop, although my wallpaper wasn't there and I noticed the network icon in the system tray showed 'disconnected' even though I was plugged in. I got a few error messages about apt-get-repository and cinnamon.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So here's what's happening now:[/FONT][/COLOR]

[LIST=1]
[*]sudo isn't working. If I type any command with sudo, I just get a cursor on the next line which hands indefinitely

[*]My internet isn't working, seems as if my network card hasn't been detected. ifconfig does the same thing as sudo too, i.e. hangs indefinitely.
[/LIST]
[COLOR=#000000][FONT=Arial]Here's the output of strace sudo[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][http://tny.cz/babce138](http://tny.cz/babce138)[/FONT][/COLOR]

---

### Post by ibjsb4 on 2013-10-01
Without sudo, you can't do a lot.  So I wonder if it will work in console.  Try:

Ctrl + Alt + F1

Try using sudo.

To excape console and return to GUI:

Ctrl + Alt + F7

---

