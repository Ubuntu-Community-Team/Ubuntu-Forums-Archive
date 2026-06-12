---
title: "VNC questions"
date: 2007-07-29
forum: General Help
---

### Post by clievers on 2007-07-29
Hi there. I've just installed Ubuntu Feisty Desktop on a couple of boxes. I've noticed that I can go in and turn on Remote Access, so from my Windows box, use RealVNC viewer to connect.

My first question is, what is the vnc server that is installed with Ubuntu Feisty? I am wondering, because if I search for 'vnc' in synaptic, "vnc-common" is installed but not the "vnc4server" So what is actually the server? I ask, because I'd like to uninstall it and replace it with something else less intensive. ?? If I connect to the vnc, my processor spikes to around 50% to control the session, so I was hoping there would be a different server out there that's less resource intensive. Also, I've modified my default runlevel (runlevel 2) to not load 'gdm', therefore it loads to console only (if i want gnome, i just execute 'sudo init 3'). In this case, I can't even connect to vnc, so I am looking to do this as well. For the most part, I won't need the gnome desktop, especially if I can just connect to vnc.

Any suggestions on how to configure this, change servers, etc? :confused:
Thanks very much.

---

### Post by clievers on 2007-07-30
Upon doing more researching,  I've finally found the answer to one of my questions: that vino is the default VNC server for GNOME. I see that though you need to already be in a gnome session for it to work. My other questions still apply though, which server to use so that i can be in console mode and still get a vnc session.
Thanks.

---

### Post by frafu on 2007-07-30
Hello, 

If you don't mind using propriety software, you can use NX from [nomachine]("http://www.nomachine.com/") to create remotely a graphical session. They also offer a free edition that should suffice for private  usage. (I am using it.) It is even faster than vnc. There is also a freenx, which is based on it. 

Francesco

---

### Post by microbyte on 2007-08-02
Okay, I tried installing the files, and they appeared to work (The only problem it had was with CUPS, which isn't really an issue for me), and then it was done.

I can't figure out now how it is set up. There isn't any graphical stuff in my menu's, and I'm feeling rather clueless.

Any help you can give?

---

### Post by dannyboy79 on 2007-08-02
my suggestion, only open 1 port on your computer or firewall, a ssh port. then install openssh-server, secure it with public key pair WITH a passphrase. then you can tunnel in with an ssh client and port forward local ports to your remote machine. this will then allow to have totally secure encrypted connections with any protocol you want, like VNC, POP, HTTP, or whatever! I myself use x11vnc as my vnc server because it allows me access to the current session that's already running, then on the windows side (since I am at work) I just double click on tightvncviewer (no app to install) from my usb stick and there's my Ubuntu desktop sitting in front of me. It's VERY secure, no ssh client or vncviewer to install at work, and it allows me to access what I was already working on at home.

NXserver, NXnode, NXclient is suppose to do that same thing (secure it thru ssh tunnel) but I found it didn't work with passphrase protected keys and you have to install the client on the remote machines which wouldn't work for me. can't install on work computer, it's blocked.

good luck

---

