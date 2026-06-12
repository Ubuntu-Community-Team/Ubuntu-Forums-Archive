---
title: "Low performance when booting headless"
date: 2017-08-24
forum: General Help
---

### Post by alku1 on 2017-08-24
I just setup a new Ubuntu 16.04 from scratch.

hardware spec:
Intel Pentium G9300
  MSI H110I Pro
  ADATA SX7000 M.2 128 GG
  G.Skill 4 GB DDR4
PCIE LSI Raid Controller

I installed everything while having a monitor and keyboard/mouse connected locally. Everything works like a charm. But here is the catch.
As soon as I reboot without monitor and the peripherials, I observe super low performance working remotely. Everything takes 5-10 seconds delay and windows opening in slowmotions. I tried VNC as well as teamviewer, both show the same result :( In fact, I cant work with it because opening terminal and using commands is already too much delay... 

Here my observations:


[LIST]
[*]booting with peripherials everything works flawlessly. Even when disconnecting peripherials and working remotely. 
[*]booting without peripherials leads to the above-mentioned extremly low performance. 
[*]Once I connect the peripherials locally again, everything works fine on the local machien (even without reboot) 
[/LIST]

I suspect that it might have something to do with the graphics acceleration?! No clue but its super frustrating.

Any suggestions what to try?

---

### Post by TheFu on 2017-08-24
Use ssh.

---

### Post by alku1 on 2017-08-27
Oh come on. I switched to Linux from Windows and now I have these ridiculous issues?! :P
I need a desktop so SSH only is not an option. Now I ordered an HDMI dummy which is supposed to fix that issue, lets see. But still awful that somewthing like cant be managed on OS level.

---

### Post by TheFu on 2017-08-27
"Oh come on?"  Srsly?

The GUI is not part of the OS on Unix systems.  It is an add-on.  Because of the architecture for Linux, we get to have many different GUIs or no GUI if that makes more sense.  This allows Linux to be used on a $5 computer or pretty much anything costing more, without a GUI.

Unix systems are used around the world remotely over ssh every day. ssh is a way of life, because it is generally secure (use ssh-keys, never passwords) and fast and works well on low-resource computers.  It works over dial-up or 40Gbps connections. There are tools around keeping the connections up (tmux, screen) so running tasks get to completion regardless of the remote connection state.

When you said "remote" - I assumed more than 50 ft away with unknown bandwidth.  ssh is the best choice.

However, there are much better methods that VNC or teamviewer (for certain values of "better").  I have NEVER used teamviewer and stopped using VNC about 8 yrs ago after discovering the NX protocol for a remote desktop.  My normal desktop is running inside a KVM VM on a system without any GPU, using x2go.  x2go is 2x-3x faster than other options I've tried.  It uses ssh for the secure tunnel.  **Setup ssh first, before installing x2go.**  It would be preferable to setup ssh-keys between the client and server too.  x2go honors those keys and settings in the ~/.ssh/config file.
[https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/](https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/) explains the installation. Don't think it has changed in 16.04, but I don't have many 16.04 systems.  Don't use a complex GUI like Unity with x2go.  Use something like XFCE, LXDE, or Mate instead.  x2go lets us tell the connection how much bandwidth is available and set the compression settings for that.  For productivity applications, ISDN is great.  Word processing, spreadsheets, stuff like that all work fine over x2go.  I've use it from halfway around the world and it wasn't bad.
x2go does have limitations. Some of the options require 2-way ssh. If you don't control the router ports on both sides of the connection, they will not work.  Also, don't expect video to work well.  You might try it from a cafe down the street, we all do, but it will be painful.  On a fast LAN, it might work, but I wouldn't call it good.  

If you are on the same LAN as the other system, you can use X-Forwarding, which is built-into ssh.  This is much easier than setting up x2go.  It is extremely common, but due to the X/Windows protocol, really needs to be on a 100Mbps connection to be used.  **ssh -X userid@IP command** is the general format and REQUIRES the local machine be running an X/Server.  Windows doesn't have an X/Server, but every Linux desktop does.

Expecting Linux to work like Windows will lead to frustration, BTW. 90% of the power of Linux/Unix systems comes from using automation and the CLI.  [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

BTW, I googled and didn't see anything about a G9300.

---

### Post by gordintoronto on 2017-08-27
It's got to be a Q9300 Core 2 Quad, and it's a current product.

I have observed that some computers function very poorly *at the hardware level* with no keyboard attached. Plug in a keyboard, boot up and all is well.

---

### Post by TheFu on 2017-08-28
Or it is a Pentium G3900?  The G3900 is faster than a 1st gen Core i5. Pentium G-series stuff isn't all that low end, though some of the prices are VERY low. ;)

I've never seen the keyboard issue on non-Windows machines.  Pretty much all my systems boot with keyboard, mice, or video. MSI, Asus, Gigabyte, Intel motherboards.  Well ... let me check on my MSI system.  USB3 storage on it has been slow, but my analysis said it was due to the internal PCI being flooded with more data than it could handle.

Live and learn.

---

### Post by HermanAB on 2017-08-28
The UNIX philosophy is different.

Your local machine already has a desktop.  It is pointless to overwrite the local desktop with a slower remote desktop, sending all the remote graphics over the wire.

It is more efficient to run the remote programs transparently on the local desktop using SSH.

---

### Post by rnctx on 2018-05-22
All the responses to this thread are pointless, but I can confirm the same issue as the OP.

This same issue affects me on 16.04.  I installed the base OS quite some time ago without a desktop, which was installed later with a temporary monitor/keyboard attached.  As soon as I rebooted it headless, the desktop performance went to the trash.  4-5 second delay to click on a button over a local gigabit network.

---

### Post by QIII on 2018-05-22
Good night, old thread.

Closed.

---

