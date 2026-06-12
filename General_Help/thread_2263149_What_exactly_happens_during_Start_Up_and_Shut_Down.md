---
title: "What exactly happens during Start Up and Shut Down Ubuntu HDMI CEC?"
date: 2015-01-29
forum: General Help
---

### Post by jeffmezz on 2015-01-29
I need to know what exactly is telling my HDMI switch to switch when my PC is turned on. The reason I need to know this is that when my PC sleeps and I try waking it via moving the mouse or keyboard presses nothing happens it stays on the active viewport in my case Amazon FireTV...The only way I can switch back to PC display is forcing a Restart... When it Restarts sure enough the switch switches to the PC as the active device. I would like to make a keyboard shortcut like Ctrl+Shift+S to send a CEC start signal to emulate startup for wake...Is this possible?...

---

### Post by efflandt on 2015-01-30
Not even sure it Ubuntu has anything in standard packages for CEC control. For example in 14.04:```
efflandt@XPS-8100-1404:~$ apropos cec
cec: nothing appropriate.
```And if I search for cec with Quick filter of synaptic it just shows cec-utils (This library provides support for the Pulse-Eight USB-CEC adapter.) and some other stuff unrelated to HDMI CEC.

Although, maybe cec-utils is what you are looking for, because this page gives some info about cec-client from cec-utils [URL="http://manpages.ubuntu.com/manpages/trusty/man1/cec-client.1.html"]http://manpages.ubuntu.com/manpages/trusty/man1/cec-client.1.html
[/URL]
I guess I should look into that, but I just turn on my HDTV with its remote when booting or it it has gone to sleep after not receiving a video signal for 10 minutes. I know that my LG HDTV can do some things with CEC from using my TV remote to do things when a Raspberry Pi is running XBMC.

PS: I tried installing cec-utils, but cec-client -l did not find anything. From web searching cec-utils apparently it does need the Pulse-Eight USB-CEC adapter, so it does not work with HDMI CEC directly.

---

