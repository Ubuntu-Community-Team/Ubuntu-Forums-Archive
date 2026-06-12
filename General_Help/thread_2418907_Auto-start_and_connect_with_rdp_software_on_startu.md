---
title: "Auto-start and connect with rdp software on startup help"
date: 2019-05-13
forum: General Help
---

### Post by cheezeh3d on 2019-05-13
So I got ubuntu a few days ago and I was trying to see if I could connect to my ubuntu machine at home from my laptop at any location. I found a lot of stuff that allows you to use rdp and connect to the computer using a software (I have looked at things like [xrdp]("http://www.xrdp.org/"), [remmina]("https://remmina.org/"), and [RealVNC]("https://www.realvnc.com/en/")), but I am the kind of guy to make everything really complicated and I wanted to take it a step further. What I'm trying to have happen is when I start my laptop I can either automatically connect to my main computer with rdp and control my stuff over there without the hassle of opening the program, inserting the ip, etc etc etc. I realized that I could pay for as cloud desktop and connect to a server, but I am cheap and don't have money to spend like that XD. So I am looking for a free way to automatically have my laptop on startup connect to my desktop at home. Again, I am very new to ubuntu, so I apologize if I am not being very clear with this. Anybody know of any way to make this happen?

---

### Post by dragonfly41 on 2019-05-14
> [COLOR=#000000]automatically have my laptop[/COLOR]

I read this as you requiring some means of automating desktop processes.

Although a bash or python script (or even ansible script) could be written to launch as startup there is a useful GUI which I use (and it is found in Ubuntu Software Centre if you have installed synaptic).

[https://wiki.actiona.tools/doku.php?id=:en:start](https://wiki.actiona.tools/doku.php?id=:en:start)

Or ```
sudo apt-get install actiona
```

There is a bit of a learning curve but you can write a series of actions as though using Ubuntu in "autopilot mode".
Each action is a Qtobject and can be accessed by javascript chunks.

Walk through a manual exercise first and take note of each discrete step (action).

The end automation script (*.ascr) can then be run by using the command ..

```
actexec <path-to-your-*.ascr-file>
```

If you have used Windows the equivalent app is autohotkey.

===========================

[P.S.] Another option to explore is TeamViewer.

[https://ubuntuforums.org/showthread.php?t=2417944&highlight=teamviewer](https://ubuntuforums.org/showthread.php?t=2417944&highlight=teamviewer)

---

### Post by cheezeh3d on 2019-05-14
Sweet I will look more into this. Thanks for the reply!

---

### Post by TheFu on 2019-05-14
Please don't allow remote desktop access over the internet to your system(s) without using either a VPN that terminates at your home or an ssh-tunnel.  Thousands of home systems are hacked every hour because they do stuff like this.  A password to connect to the VNC/RDP session is NOT sufficient security.

The easiest, secure, solution is to run x2go-server on the remote system and use the x2go-client.  x2go uses the NX protocol, which uses ssh authentication and encryption.  Only the ssh port needs to be open on the server and ssh-key-based authentication should be used over the internet, never passwords.

The first step is to get plain ssh working with key authentication. Once that works, x2go will work easily.

---

### Post by cheezeh3d on 2019-05-14
Got it thanks for the heads up

---

