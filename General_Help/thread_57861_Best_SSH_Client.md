---
title: "Best SSH Client"
date: 2005-08-18
forum: General Help
---

### Post by horeon on 2005-08-18
Hello,

I'm looking for a good ssh client like putty  with something like quickputty...

Where can I find putty in gtk2.x or/and to another good software to do ssh connection easly?

Thanks

---

### Post by heimo on 2005-08-18
Welcome!

There seems to be [putty]("http://packages.ubuntu.com/hoary/net/putty") in [universe]("https://wiki.ubuntu.com/UniversePackages"). Use Synaptic Package manager (graphical, in administration menu) or apt-get to install it (on terminal: sudo-apt-get install putty). You need to enable universe to do that.

I haven't used putty on Linux, so if you try, could you share your impressions?



EDIT. Just noticed 'quickputty', I don't know what that is, so hopefully my reply wasn't too much off. EDIT2: And it seems to use old gtk.

---

### Post by slux on 2005-08-18
Linux putty is for GTK 1.x so if you're bothered by somewhat ugly widgets, it doesn't do the trick.

I believe there may be another frontend or two although I don't think they're in Ubuntu, but seriously:

why even bother? ssh <hostname> from a shell seems more than adequate for me. You're going to use a command line anyway after you've made the connection so I have some issues with anyone claiming that it's too hard and I don't really understand what added convenience is there.

---

### Post by WirelessMike on 2005-08-18
[QUOTE=slux]Linux putty is for GTK 1.x so if you're bothered by somewhat ugly widgets, it doesn't do the trick.

I believe there may be another frontend or two although I don't think they're in Ubuntu, but seriously:

why even bother? ssh <hostname> from a shell seems more than adequate for me. You're going to use a command line anyway after you've made the connection so I have some issues with anyone claiming that it's too hard and I don't really understand what added convenience is there.[/QUOTE]

Agreed.  I've used both putty and traditional ssh in the command line.  In regards to ssh, I don't really see much value added with putty.  The tool was originally intended for Windows and in my experience, the value that is obvious there doesn't exist on a terminal interface as powerful as that on Linux.  As a matter of fact, I think the fact that ssh and openssh don't require gtk dependencies is added value over putty.

---

### Post by npaladin2000 on 2005-08-18
PuTTy allows easy management of multiple connections and their associated settings through a GUI, whereas commandline ssh doesn't.

---

### Post by arnieboy on 2005-08-18
gftp is ur best bet and it uses gtk2. try it.
```
sudo apt-get install gftp
```

---

### Post by celloandy on 2005-08-18
[QUOTE=arnieboy]gftp is ur best bet and it uses gtk2. try it.
```
sudo apt-get install gftp
```[/QUOTE]

gftp is an FTP program, and while it does support file transfers via SSH, it has no support for actual SSH sessions, at all, as far as I can tell.  He's looking for an actual SSH client, like putty.

As far as my recommendations, I'm generally a fan of the regular OpenSSH client, too, and don't know of any good GTK+ frontends, except for putty.  The only program I could find that does anything like what you want is gcrm, and it just saves connection information and uses it to launch the OpenSSH client in a terminal.  Plus, the interface is really clunky.  Sorry!

Andrew

---

### Post by shakin on 2005-08-18
$ sudo apt-get install secpanel

Works well for me.

---

### Post by arnieboy on 2005-08-18
[QUOTE=celloandy]gftp is an FTP program, and while it does support file transfers via SSH, it has no support for actual SSH sessions, at all, as far as I can tell.  He's looking for an actual SSH client, like putty.

As far as my recommendations, I'm generally a fan of the regular OpenSSH client, too, and don't know of any good GTK+ frontends, except for putty.  The only program I could find that does anything like what you want is gcrm, and it just saves connection information and uses it to launch the OpenSSH client in a terminal.  Plus, the interface is really clunky.  Sorry!

Andrew[/QUOTE]
I will rephrase myself. gftp lets u do all that u wud want to do from an SFTP client like download, upload, remove, create, rename and manipulate files and directories in general.

---

### Post by kvidell on 2005-08-18
[QUOTE=npaladin2000]PuTTy allows easy management of multiple connections and their associated settings through a GUI, whereas commandline ssh doesn't.[/QUOTE]
 Sure it does :) You just have to know how to setup the ssh config file :)

You can set port forwards, X Forwarding, Tunnels and all kinds of other stuff in the config file per host.
You can even set different user names to use per host.
Then all you have to do is ssh hostname :)
- Kev

---

### Post by horeon on 2005-08-19
I use putty with quickputty ([http://www.deckmyn.org/olivier/software](http://www.deckmyn.org/olivier/software)) under windows because it's very easy and quickly to manage all sessions with forwarders ports, X forward, And Setting default Variables.

But don't find something like it under linux :(
Putty works well under linux but have some problems with encoding and others minors bugs and have a crap GUI in gtk1.

The best will be a putty in GTK 2.x with all same options as under windows version.
And a rewriting code of quickputty to run inside gdesklet :D

---

