---
title: "looking for a remote control program"
date: 2007-02-13
forum: General Help
---

### Post by nick3295 on 2007-02-13
hi people,

I'm looking for a remote control program, that lets me control my ubuntu 6.06 PC from elsewhere. It would be preferable if I could control it from a windows PC and if it's free.

thanks

---

### Post by phiphedog on 2007-02-13
I use vncserver and it works fine and I can access it from my windows PC at work.

[COLOR="red"]apt-get install vncserver[/COLOR]

and then when you run it from a cmmandline with the command [COLOR="Red"]vncserver [/COLOR]it will ask you to set up a password.

note: when connecting I need to add the display number to the ip address like this 203.22.135.22:1

---

### Post by Marsolin on 2007-02-13
You'll also need a VNC client to run on Windows.  I've used TightVNC and RealVNC before.

Another option is to use NX.  It's faster than VNC, but a little harder to set up.  Server options include [NX Server]("http://linuxappfinder.com/package/nxserver"), [FreeNX]("http://linuxappfinder.com/package/freenx"), or [2X TerminalServer]("http://linuxappfinder.com/package/2xterminalserver"). The [NX Client]("http://linuxappfinder.com/package/nxclient") is available for both Linux and Windows.

---

### Post by nick3295 on 2007-02-14
thanks for the help :)

---

### Post by Jason Weiss on 2007-03-01
ok I Just want to make sure we are talking about the same thing I have 5 computer I am planning to give to my idiot friends, they know nothing about computers, so I am preinstalling the computers with ubuntu.

I wouls like to be able to log in to their computers and work on them remotely over the internet. 

So I need vncserver is that right?

---

### Post by maniacmusician on 2007-03-01
> **Jason Weiss said:**
> ok I Just want to make sure we are talking about the same thing I have 5 computer I am planning to give to my idiot friends, they know nothing about computers, so I am preinstalling the computers with ubuntu.

I wouls like to be able to log in to their computers and work on them remotely over the internet. 

So I need vncserver is that right?
That's one of the options. If you just need command line access, then you just set up an ssh server.

---

### Post by Jason Weiss on 2007-03-01
No Command line is exactly what I want

so if I only use ssh, can I do everything I normally do in terminal on thier computer, ie logging in as root?

---

