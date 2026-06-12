---
title: "Forcing XRDP to use an existing Xorg server"
date: 2023-05-25
forum: General Help
---

### Post by linuxnewbie23 on 2023-05-25
Hi, 

I run a Ubuntu 22.04 server with lubuntu desktop (LXQT). I have installed the latest XRDP using the extremely useful scrip provided by c-nergy.be. From time to time though XRDP will stop passing through the clipboard. When this happens I just do a systemctl restart xrdp and that fixes the clipboard issue. However, when I restart xrdp lose my rdp session with all my windows and apps that are running. 

I discovered that when I start an RDP session to the server xrdp sets up a Xorg server:
[I]/usr/lib/xorg/Xorg :10 -auth .Xauthority -config xrdp/xorg.conf -noreset -nolisten tcp -logfile .xorgxrdp.%s.log

[/I]When I gracefully close my RDP client, *Xorg :10 *remains active, which means when I launch my RDP client again, I get connected to my last session with all my windows and apps still open. But if I have to restart XRDP using systemctl XRDP creates Xorg :11 despite Xorg :10 still being there. When I launch my RDP client after the restart, I get connected to Xorg :11. 

I have spent the last few days researching the web and trying various suggestions related to sesman.ini, xrdp.ini and xorg.conf. These are just some of the suggestions I tried. I have even asked chatGPT!!

[https://github.com/neutrinolabs/xrdp/issues/960](https://github.com/neutrinolabs/xrdp/issues/960)
[https://askubuntu.com/questions/133343/how-do-i-set-up-xrdp-session-that-reuses-an-existing-session](https://askubuntu.com/questions/133343/how-do-i-set-up-xrdp-session-that-reuses-an-existing-session)

Sadly I am no closer to forcing XRDP to reuse the initial Xorg server it created. I hope someone here has solved this issue and can share their solution. Thank you

---

### Post by MAFoElffen on 2023-05-26
In /etc/xrdp/xrdp.ini, change this line 
```

port=-1

```
Which tells xrdp to always look for an open port, to
```

port=5912

```
Which will tell xrdp to always use the same port number, '5912'... It will then only use that port.

---

### Post by linuxnewbie23 on 2023-05-26
Hey 

Thanks for the response. Unfortunately it wouldn't initiate a RDP session with that change. xrdp.log doesnt show any errors and sesman.log doesnt show any activity at all with your proposed changes. Looks like it doesnt even try and set up a xorg server.

---

### Post by MAFoElffen on 2023-05-26
Let me setup an XRDP session with one of my VM's and see which specific port it uses, to set to it... I'll test that to verify that works.

---

### Post by TheFu on 2023-05-26
If you aren't tied to **xrdp**, there are other, more secure, remote desktop options which allow different sessions or reconnecting to the same session from anywhere ... with all the programs/desktop left as it was.  ssh is used for connection credentials and encrypted security and the desktop is highly compressed to feel much faster than either xRDP or VNC options.  

But if you must use RDP, I cannot help. Sorry.

---

### Post by linuxnewbie23 on 2023-06-07
[COLOR=#000000][INDENT]Let me setup an XRDP session with one of my VM's and see which specific port it uses, to set to it... I'll test that to verify that works.[/INDENT]
[/COLOR]

Thanks - were you able to set up a test session?

---

### Post by linuxnewbie23 on 2023-06-07
> **TheFu said:**
> If you aren't tied to **xrdp**, there are other, more secure, remote desktop options which allow different sessions or reconnecting to the same session from anywhere ... with all the programs/desktop left as it was.  ssh is used for connection credentials and encrypted security and the desktop is highly compressed to feel much faster than either xRDP or VNC options.  

But if you must use RDP, I cannot help. Sorry.

Thanks - unfortunately I'm tied to RDP

---

