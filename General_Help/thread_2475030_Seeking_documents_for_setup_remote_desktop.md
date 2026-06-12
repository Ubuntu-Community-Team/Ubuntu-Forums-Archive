---
title: "Seeking documents for setup remote desktop"
date: 2022-05-14
forum: General Help
---

### Post by satimis on 2022-05-14
Hi all,

Please help me to find document re setup of remote desktop on Ubuntu 20.40 desktop PC.

Remote Desktop Feature:
PC1 remotely operates PC2/Android Phone.  The desktop of the later is displayed on PC1.

I found following links;

How to Install Xrdp on Ubuntu 20.04
[https://www.tecmint.com/install-xrdp-on-ubuntu/](https://www.tecmint.com/install-xrdp-on-ubuntu/)

Access a remote desktop
[https://ubuntu.com/tutorials/access-remote-desktop#1-overview](https://ubuntu.com/tutorials/access-remote-desktop#1-overview)

How to Install Xrdp Server (Remote Desktop) on Ubuntu 20.04
[https://linuxhint.com/install_xrdp_server_ubuntu/](https://linuxhint.com/install_xrdp_server_ubuntu/)

I have done this kind of setup long time ago and couldn't locate their document on my database.

What I'm going to achieve is as follows;
I use Samsung smart phone to digitize/scan old color film negatives.  For its feature pls refer to following link;
How to scan film negatives with FilmBox?
[https://www.youtube.com/watch?v=MDbosI2VuUw](https://www.youtube.com/watch?v=MDbosI2VuUw)

It is now working without problem, digitizing film negatives and saving the files on the smart phone

Now I need to remotely control the Samsung smart phone on Ubuntu 20.04 desktop PC, operate the scanning and display the smart phone desktop on the display of Ubuntu 20.04 desktop PC via Internet/WiFi.  Please help me to find relevant documents/links re their setup.

Thanks in advance.

Regards

---

### Post by TheFu on 2022-05-14
For android, there are specific tools.  **scrcpy** is one. There's a snap. I works on some of my systems, but not all.  Also, audio is not transferred to the PC, so you'll want the phone nearby.  I've tested it with USB connection, but think it works over a LAN network connection, but definitely NOT over a cell data connection.  It is good enough for playing games, so I think it will be good enough for scanning stuff.  I really like your use-case. Smart.

I have a USB negative and slide scanner. Think it was $100. It came with WinXP software that never worked on Vista or later PCs, but it is plug-in-play with Linux and whatever scanner software is used.  The quality is fine, not great.  I had an expensive Epson negative and slide scanner and page scanner, but it was huge and slow.  In the time It would take to scan 5 slides, I could to at least 20 in the USB thingy.  *Perfect is the enemy of done.*

For remote desktops, I'm a little disappointed that you don't list x2go.  The only problem with x2go is that it doesn't like Gnome3+ or Wayland.  Do you really even need a full remote desktop?  Just use **ssh -X** forwarding, especially if you are on the same LAN.  It is trivial and 'just works'.  It has been working as long as ssh has existed.

I wrote a few blog articles about this stuff years ago to explain the options.  [https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)
> 99% of the time, I use `ssh -X` to remotely start remote applications and have them displayed on my current machine.
I show exact commands for using ssh X11 forwarding.
If you still want a full desktop, see the section labeled: _NX Based Remote Desktops : 12/2014 Update_ in that link.

[https://blog.jdpfu.com/2012/10/23/remote-desktops-rock](https://blog.jdpfu.com/2012/10/23/remote-desktops-rock) is about running a remote desktop to run a remote desktop. It works.laptop
```

|____via_NX
     |____Linux-VM
          |____via_RDP
               |____Win7-MC-VM
```

---

### Post by satimis on 2022-05-14
> **TheFu said:**
> For android, there are specific tools.  **scrcpy** is one. There's a snap. I works on some of my systems, but not all.  Also, audio is not transferred to the PC, so you'll want the phone nearby.  I've tested it with USB connection, but think it works over a LAN network connection, but definitely NOT over a cell data connection.  It is good enough for playing games, so I think it will be good enough for scanning stuff.  I really like your use-case. Smart.
- snip -

Hi,

Thanks for your detailed advice.

What I expect to do is;

1) I have FilmBox, a film negative scan software, installed on Android Phone
2) To scan the film negative
Place the film negative above a light box
Hold the Android Phone above the film negative
Press and hold the Red Button on Android Phone screen to scan
(pls see following link;
How to scan film negatives with FilmBox?
[https://www.youtube.com/watch?v=LPDA_A8u-8Y](https://www.youtube.com/watch?v=LPDA_A8u-8Y)
)

Now I expect to scan remotely on a desktop PC, pressing and hold the red button on PC display.  Please see the attached photo showing the screen of the Android Phone

Regards

---

