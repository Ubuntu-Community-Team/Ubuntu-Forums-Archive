---
title: "SSH Xwindow login question?"
date: 2013-09-11
forum: General Help
---

### Post by robn30 on 2013-09-11
So I have a question regarding how to remotely login to X by way of SSH.  If I connect to my remote machine by way of SSH but X is not running and the machine is sitting at the Gui Logon screen, can I enable X so I can connect using x11vnc?  If so how do I do this.  I have no problems with SSH or X11VNC as long as someone is logged into X, it works perfectly.  I want to know how to force login if X is not currently running.  Thanks.

---

### Post by 1clue on 2013-09-11
I'm confused as to what you want.

There's no need for the X server to be running on the remote machine.  The remote machine needs X clients (firefox, file browser, etc) but the X server is on your workstation.

X client-server relationship is reversed from the intuitive way of thinking.  The "client" is the application which wants to draw a window.  The "server" is the X framework, window manager with the buttons on it, with keyboard and mouse input.

X11vnc is only good for workstations which have VNC installed and no X, and you want to run something on the server.  It's limited to one session per server AFAIK, so it's just about useless IMO.

X supports many sessions simultaneously, with many users.

Or are you saying you want your workstation to be a dumb terminal and show the X login screen of your server?  So there is no real functionality on your workstation other than the video/keyboard/mouse?  That's XDMCP.

---

### Post by CaptainMark on 2013-09-12
Instructions for using VNC before a user is logged in are on the Wiki for VNC, [https://help.ubuntu.com/community/VNC#accessing-family-pc](https://help.ubuntu.com/community/VNC#accessing-family-pc)

---

### Post by 1clue on 2013-09-12
Looking at what you're saying, I think you just want to log into your remote box from your workstation.  X11vnc has nothing to do with ssh really, so let's just ignore it and get on with your problem.

What OS are you using on your local system/workstation?

If you're on Linux and have a desktop system (NOT, for example, Ubuntu Server) then you have an X server already running.
If you're on Mac OS X then you MIGHT have one, the best right now is XQuartz.  Google is your friend if you don't have it.  Mac OS will automatically start the X server when you need it.
If you're on Windows then no standard X server comes with your system, but I know there are several available.  You need one.  If it doesn't start automatically then you'll need to have it running before you try to make an X call.

So getting on to it:

ssh -X *user*@[I]your_server
[/I]
The -X is capital.

Now, run whatever app you want.  Firefox, or *sudo synaptic,* or whatever.

If you're running Windows as your desktop, I don't know exactly how that works.  Somebody here surely does.

Here's what you need to understand:
The windowing system on your remote machine has NOTHING to do with the windowing system on your workstation.  You need not even have an X server installed on your remote machine, if it's headless.  The X server can exist but need not be running.  Or someone can be logged in and using it.  It's irrelevant to your logging in with a remote session.

UN*X, including Linux, is a multi-user multitasking operating system.  The number of people logged in with windowing apps on your system is limited only by the amount of memory, networking speed and other resources your system has.  Linux does not limit that sort of thing.

---

### Post by robn30 on 2013-09-12
> **1clue said:**
> I'm confused as to what you want.

There's no need for the X server to be running on the remote machine.  The remote machine needs X clients (firefox, file browser, etc) but the X server is on your workstation.

X client-server relationship is reversed from the intuitive way of thinking.  The "client" is the application which wants to draw a window.  The "server" is the X framework, window manager with the buttons on it, with keyboard and mouse input.

X11vnc is only good for workstations which have VNC installed and no X, and you want to run something on the server.  It's limited to one session per server AFAIK, so it's just about useless IMO.

X supports many sessions simultaneously, with many users.

Or are you saying you want your workstation to be a dumb terminal and show the X login screen of your server?  So there is no real functionality on your workstation other than the video/keyboard/mouse?  That's XDMCP.

> **CaptainMark said:**
> Instructions for using VNC before a user is logged in are on the Wiki for VNC, [https://help.ubuntu.com/community/VNC#accessing-family-pc](https://help.ubuntu.com/community/VNC#accessing-family-pc)

> **1clue said:**
> Looking at what you're saying, I think you just want to log into your remote box from your workstation.  X11vnc has nothing to do with ssh really, so let's just ignore it and get on with your problem.

What OS are you using on your local system/workstation?

If you're on Linux and have a desktop system (NOT, for example, Ubuntu Server) then you have an X server already running.
If you're on Mac OS X then you MIGHT have one, the best right now is XQuartz.  Google is your friend if you don't have it.  Mac OS will automatically start the X server when you need it.
If you're on Windows then no standard X server comes with your system, but I know there are several available.  You need one.  If it doesn't start automatically then you'll need to have it running before you try to make an X call.

So getting on to it:

ssh -X *user*@[I]your_server
[/I]
The -X is capital.

Now, run whatever app you want.  Firefox, or *sudo synaptic,* or whatever.

If you're running Windows as your desktop, I don't know exactly how that works.  Somebody here surely does.

Here's what you need to understand:
The windowing system on your remote machine has NOTHING to do with the windowing system on your workstation.  You need not even have an X server installed on your remote machine, if it's headless.  The X server can exist but need not be running.  Or someone can be logged in and using it.  It's irrelevant to your logging in with a remote session.

UN*X, including Linux, is a multi-user multitasking operating system.  The number of people logged in with windowing apps on your system is limited only by the amount of memory, networking speed and other resources your system has.  Linux does not limit that sort of thing.

I knd of knew my question was going to be a little confusing as I am a noob for the most part.  Although I have been using Ubuntu for a few years, I am more of a user than a super knowledgeable about all things user.  CaptainMark was right on point with what I was trying to do.  Clearly my terminology was way off when I said X window.  I can SSH into my machine while it is at the login greeter but I couldn't get X11vnc running.  So I was looking for a way to get x11vnc running so I could log the machine in.  I will try to follow the instruction in the link and see if that works for me.  If not I will be back for sure for more questions.  I am learning but it is a long process.  Thanks for the replies!

---

### Post by robn30 on 2013-09-12
All figured out, CaptainMark provided the perfect link for what I needed.  Everything is working perfectly now.  Thanks again to all the folks here that help us inexperienced users learn and get more proficient.

---

### Post by HiImTye on 2013-09-12
it's much simpler to use RDP, as it creates it's own login environment and starts the desktop automagically, but I'm glad you found what you were looking for.

---

### Post by CaptainMark on 2013-09-13
> **1clue said:**
> X11vnc has nothing to do with ssh really,
That only holds true for using vnc within your own local network, anyone trying to use any vnc software over the internet should be looking at sending the vnc connection through an ssh tunnel, I wouldn't consider any other method to share an X server over the internet.

---

### Post by robn30 on 2013-09-17
> **CaptainMark said:**
> That only holds true for using vnc within your own local network, anyone trying to use any vnc software over the internet should be looking at sending the vnc connection through an ssh tunnel, I wouldn't consider any other method to share an X server over the internet.

Agree with CaptainMark, I am using this both locally, and remotely over the internet to help my parents when they have computer issues.  I don't want any snooping so its SSH tunneled with RSA encryption.

---

### Post by 1clue on 2013-09-17
I think you've taken my statement as out of context as it's possible to take it.  Frankly I wouldn't consider using ANY network technology with personal data over the greater Internet without encryption.  My statement was made when I thought the OP just wanted to get a windowing app going from a remote box.

My personal solution would never include X11vnc.  I've installed it and tried it, and found it to be either entertaining or irritating depending on the situation.  IMO it has all the utility of xeyes.

My remote sessions are all ssh -X <hostname> and then just pipe X apps back through the ssh tunnel.  Nothing more needs to happen.  *buntu is already set up to handle it on both ends, all you need is ssh client and an X server on the workstation, and X apps on the remote box.

So when I said 'ignore it' I meant 'ignore X11vnc' not 'ignore ssh'

---

### Post by 1clue on 2013-09-17
X11vnc supports exactly one session per server.  This is just fine for a system which only one person has access to, but not helpful at all if it's a business or even a family.

X11vnc is useful only in a situation where the remote system does not have an easily available X server.  That means a Windows box, unless there's a really simple X server since last I looked some years ago.  However, since you have to install vnc on the windows box, AND you would have to install an X server on the windows box, then it's really the same thing there.

Linux is multi-user and multitasking.  You can have as many remote sessions as you have memory and CPU and network bandwidth for.  Some or all of these can have windowing apps going.  Ssh is the default networking app for that, it provides both connectivity and encryption.

Linux has and heavily uses X.  Mac OS has a good X server available for free, and you don't have to configure anything.  So aside from Windows, you don't need X11vnc.

Now, you google "free easy X server for Windows" and get all sorts of stuff.  You install Cygwin or putty and you get ssh.  So again, why install X11vnc?  Who wants a remote session where somebody sitting in the server room watches everything you do?  Who wants a remote session where you can't use it if somebody else is on the main terminal?

I'm not telling the OP that he shouldn't use X11vnc, I'm just saying it's a crippling app, and much more complicated to set up than ssh is.

---

