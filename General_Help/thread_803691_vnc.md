---
title: "vnc"
date: 2008-05-22
forum: General Help
---

### Post by mikeduffy13 on 2008-05-22
Hi all,

I'm trying to run tightvncserver for the first time and I keep getting this error.

error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I tried to dl the library listed, but it says it cannot be found. What's the issue here?

---

### Post by fragos on 2008-05-22
I use xtightvncviewer every day but didn't need to install the server. I used System-> Preferences-> Remote Desktop on the server PC and configured to allow the remote connection. I looked in Synaptic and find that vino was installed as my server.

---

### Post by HermanAB on 2008-05-22
Hmm, I always advise people to refrain from using VNC.  Rather use SSH.  It can do everything VNC does, only better and secure.

---

### Post by fragos on 2008-05-22
SSH is certainly a more secure choice over the open Internet. I only use VNC on my LAN which is protected by a firewalled router and NAT. I don't leave VNC connections up when not in use. I also power down my machines and router when not in use. No one will be hacking into my system in the wee hours when I'm sleeping. The ISP marketing departments sure didn't do the Internet community any favors when they differentiated broadband by positioning it as always on to users that didn't understand the dangers of doing so. I'm a freelance so the only disgruntled employee is me -- I'll live with that risk.

---

### Post by mikeduffy13 on 2008-05-23
> **fragos said:**
> I use xtightvncviewer every day but didn't need to install the server. I used System-> Preferences-> Remote Desktop on the server PC and configured to allow the remote connection. I looked in Synaptic and find that vino was installed as my server.

Right, I use vino right now also.  the problem with that is that you need to be logged into a session on the server to be able to access it.  It does not open new sessions...I need to be able to open new sessions without already having a user logged in.

@herman - how can you do graphical things via ssh though?  I use ssh now, but it's just command line stuff...

---

### Post by fragos on 2008-05-23
My use of VNC is between my laptop and desktop -- I'm the only user of both. There's always something more to learn.

---

### Post by bodhi.zazen on 2008-05-23
> **mikeduffy13 said:**
> Right, I use vino right now also.  the problem with that is that you need to be logged into a session on the server to be able to access it.  It does not open new sessions...I need to be able to open new sessions without already having a user logged in.

Use vncserver

[uwiki]VNCOverSSH[/uwiki]

> @herman - how can you do graphical things via ssh though?  I use ssh now, but it's just command line stuff...

ssh -X user@server

The -X option forwards the X applications. You can forward a single application or the entire desktop.

See :

[uwiki]SSHHowto[/uwiki]

[http://ubuntuforums.org/showthread.php?p=3816948](http://ubuntuforums.org/showthread.php?p=3816948)

---

### Post by mikeduffy13 on 2008-07-09
Thanks for the links to the vnc over ssh instructions.  That seems an easy way to go.  I got everything setup correctly but when I try to run the vncviewer -via command I *still* get the message
```
vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```

I don't understand why this keeps happening.  I've tried 4 different ways to connect via vnc, and the only one I don't have problems with is vino...which I can't use because it doesn't allow for new sessions...argh!

---

