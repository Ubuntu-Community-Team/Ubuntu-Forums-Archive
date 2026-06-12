---
title: "How can I run ubuntu &quot;headless&quot;?"
date: 2008-02-07
forum: General Help
---

### Post by rpardee on 2008-02-07
Hey All,

I'm wanting to dip a toe in the ubuntu waters by running it on an older machine "headless", and using remote desktop to log in & gui my way around from my main (windows xp) box.

I've gone and set the remote desktop preferences to enable connections & not ask me for confirmation, and I can VNC in just fine--so long as I'm already logged in to ubuntu.  But if I'm not already logged in, VNC comes right back with a "Failed to connect to server (blackula)" dialog.

Right now I've got the old machine hooked up to a KVM switch, so I can interact w/it directly, but I need to take this machine off the KVM & (like I say) run it headless.  Can someone throw me a clue on how to configure ubuntu to allow remote desktop connections immediately after booting up?

Thanks!

-Roy

---

### Post by bodhi.zazen on 2008-02-08
Most of us ssh into the box. If you are on Windows you can use Putty.

This gives you a command line interface, however.

Now you can forward your desktop over ssh, but you need a X server for windows. You could try Cygwin, but it may be a hassle to configure ...

An easier solution is to use an alternate VNC server, or FreeNX. 

[uwiki]VNCOverSSH[/uwiki]

[uwiki]FreeNX[/uwiki]

---

### Post by mbsullivan on 2008-02-08
Hi Roy,

From the way I'm reading it, it already sounds like you've got a VNC server running... It sounds like your VNC server daemon is not setup to start along with the computer, which is strange... I don't actually have much use for a VNC server, so I don't know the executable names, but I can hand-wave some sort of answer for you right now.

First, try going to /etc/init.d and check for some service startup script that seems to make sense, like vnc, vncd, or vnc-server. We'll configure that script to startup at every possible reasonable startup level:

```
sudo update-rc.d [script name] start 30 2 3 4 5 S . stop 70 0 1 6 .
```

Then reboot and see if you can VNC in idling at the login prompt.

Hope this helps!
Mike

---

### Post by rpardee on 2008-02-08
Thanks Guys!  Like Mike says, I'd like to have a gui on my sessions.

Alas, there was no obvious vnc shell script in /etc/init.d.  I tried perusing the running processes (this is through an active VNC session, so there's *something* serving it, right?) with a "ps aux" command, and again--nothing with 'vnc' in it.  This line caught my eye though:

/usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:Gnome_RemoteDesktopServer --oaf-ior-fd=17

(that's hand-typed, so there may be a typo in there)

So I looked for a script with vino in the name in /etc/init.d--no luck.  I grepped for 'vino' and 'remotede' in /etc/init.d and got nothing.  I grepped for just 'remote' and got tons of stuff, none of which was obviously relevant to me. :-(

(And I should have probably mentioned--I'm running ubuntu v7.10--"gutsy gibbon".)

Anybody got anything else?

Thanks!

-Roy

---

### Post by bodhi.zazen on 2008-02-08
The problem is vino, the default VNC server with Ubuntu.

With vino you need to be logged in to connect.

So... Try vncserver or vnc4server. You can then ssh into the box and start the server.

See the link I gave you for detailed directions on how to set up both Ubuntu and Windows (putty). Ask if you have a more specific question or problem.

---

### Post by rpardee on 2008-02-08
Oh drag.  Let me see if I understand you tho...

When you say you have to be logged in to use vino, you mean a full-on gnome session or whatever?  I couldn't ssh in from windows & start *that* server & then be able to connect?  But these other 2 vnc servers you mention can be started from an ssh prompt?

Thanks!

-Roy

---

### Post by bodhi.zazen on 2008-02-08
> **rpardee said:**
> Oh drag.  Let me see if I understand you tho...

When you say you have to be logged in to use vino, you mean a full-on gnome session or whatever?

That is correct, vino will on ly work after you have logged into gnome.

>  I couldn't ssh in from windows & start *that* server & then be able to connect?

Not vino

>  But these other 2 vnc servers you mention can be started from an ssh prompt?

Yes, exactly.

[https://help.ubuntu.com/community/VNCOverSSH#head-f09843431b09ba40966092f04f15548732d97fed-2](https://help.ubuntu.com/community/VNCOverSSH#head-f09843431b09ba40966092f04f15548732d97fed-2)

Everything is outlined in that link, including configuration of both your ubuntu server and windows (putty) client.

> Thanks!

-Roy

:twisted:

---

### Post by rpardee on 2008-02-08
Ah, okay then--cool.  I shall study that doc & see if I can get this together.

Thanks very much!

---

### Post by rpardee on 2008-02-08
Hey--one other thought.  Would it be possible to configure one of these alternate vnc servers to start up automagically on boot-up, so that I don't need to bother w/SSH at all?

Both the ubuntu & windows boxes are sitting behind a NAT router & don't have routable IPs.  I'm only ever going to connect from inside my (wired) network, so I don't think there is much concern over security in this situation...

---

### Post by bodhi.zazen on 2008-02-08
If you would like, add the commands to /etc/rc.local

Two comments:

1. Rebooting in Linux is uncommon, less so in servers.

2. I am paranoid and so advise you to ssh into the box and manually start the server, shut it down when done.

With that said, you are likely fine on your LAN.

If you want to get fancy, you can connect via your browser :

[http://ubuntuforums.org/showthread.php?t=541656](http://ubuntuforums.org/showthread.php?t=541656)

---

