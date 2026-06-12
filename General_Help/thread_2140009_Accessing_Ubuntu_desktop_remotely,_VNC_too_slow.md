---
title: "Accessing Ubuntu desktop remotely, VNC too slow"
date: 2013-04-28
forum: General Help
---

### Post by Lukfi on 2013-04-28
Hello.
I want to access my Linux machine remotely from my Windows PC and run graphical applications on it. It's connected via Wi-Fi 802.11g and file transfers to and from Samba run at around 2–2,5 MB/s, so not exactly fast.
I used to have a rig with Windows XP Professional on the same network and Microsoft's Remote Desktop worked fine, its performance was acceptable. I tried X11VNC server in Ubuntu. Not only does it look like crap when I limit the color palette for bandwith reasons, it's still very slow and uncomfortable to use.
Now, I've googled around a bit and found out that VNC isn't the most efficient protocol around, so apparently this is a known issue. But what are the alternatives?
I've seen people recommend TeamViewer, but that is not Linux native, requires Wine, which I don't know how to config and can't be arsed to, and also reportedly requires a fairly fast computer.
 I also learned there is something called the NX protocol, so I installed freenx on the Ubuntu PC and Nomachine NX client for Windows. The best I could get out of it was a black screen with a white terminal "window" quarter the size of the screen. Not what I'm looking for.
XRDP works out of the box, but it just wraps VNC in Windows' RDP protocol, therefore is painfully slow.

So, my question:
Is there a remote desktop software for Ubuntu, which is fast, user-friendly, accessible from a Windows client and ideally also supports clipboard transfers?

---

### Post by The Spectre on 2013-04-28
TeamViewer will work fine.

You don't need to install or configure Wine because the Wine layer is built into the TeamViewer installer.

[http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)

I have been using it for quite a While and it has worked great.

---

### Post by Lukfi on 2013-04-29
I wanted to try TeamViewer today, but I can no longer log onto the machine. Only through ssh, but not locally from the logon screen. I know, unrelated problem.

---

### Post by Lukfi on 2013-05-17
OK, so... TeamViewer does work and it can transfer files, which is good, but it is still nowhere near as fast as RDP between two Windows machines. So I guess there's no comparable solution to this :(
Is there perhaps a way to make the Wi-Fi go faster?

---

### Post by zemega on 2013-05-17
Configure your wifi manually to use 'frquency' that aren't/less occupied on both end.

---

### Post by The Spectre on 2013-05-19
I agree with [COLOR=#000000]zemega changing your Routers default Wireless Channel can make a big difference in how it performs.[/COLOR]

[COLOR=#000000]Most Wireless Routers have at least 11 Channels to chose from and by default most of them are set somewhere in the middle and if you live in an area with a lot of Wireless traffic using the same channel it will degrade your wireless performance.

Also if you are connecting to other Computers on the same Network make sure you enable the "Connection in a local network (via IP address)" in the TeamViewer Options.

[/COLOR][ATTACH=CONFIG]242762[/ATTACH]

---

