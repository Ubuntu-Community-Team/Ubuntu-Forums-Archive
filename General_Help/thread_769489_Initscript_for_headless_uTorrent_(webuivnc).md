---
title: "Initscript for headless uTorrent (webui/vnc)"
date: 2008-04-26
forum: General Help
---

### Post by samuelt on 2008-04-26
I like to be able to reach my uTorrent client where ever I am so I installed it with the webui like a lot of people have. But it's annoying to have to remember to start uTorrent after a reboot.

So I created an init-script for Ubuntu 8.04, it starts a vncserver and runs only fluxbox and uTorrent. It will start even if you don't have X running yet (or perhaps not at all). 

[Get the init-script here.]("http://pastebin.com/f577072c6")

The vnc part is so I can get access to the real thing when the webui stops working or some setting needs changing.

There are [howtos on installing utorrent in linux]("http://http://www.howtoubuntu.com/2007/10/21/how-to-install-utorrent-in-ubuntu-with-wine.html") and I use [this webui.zip]("http://blazingwolf.com/webui.zip") to get it to work in FF3b5 and Safari.

---

### Post by GrimRe on 2008-10-06
Hi,

thanks for this cool script. Unfortunately I'm having trouble installing it.

I have put the file in /etc/init.d/ do I keep the .sh file extension or not?

Either way when I try to execute it:

/etc/init.d/utorrent start

i get the message:

/etc/init.d/utorrent: /bin/bash^M: bad interpreter: No such file or directory

what could this mean?

Thanks

P.S I have changed the username in the script

---

### Post by djchester on 2009-01-07
> **samuelt said:**
>  It will start even if you don't have X running yet (or perhaps not at all). 

Hi Samuel

Will "wine /home/$USER/.wine/drive_c/Program\ Files/utorrent/uTorrent.exe >/dev/null 2>&1 &" really work without fluxbox or any X running?

Will I in that scenario need xvfb?

I really want to try this as soon as I get the hardware for this task.

---

