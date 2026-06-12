---
title: "How to access Ubuntu Desktop running in Multipass VM from macOS?"
date: 2022-06-02
forum: General Help
---

### Post by robertfdev57 on 2022-06-02
I am trying to figure out how to view Ubuntu Desktop from an Ubuntu instance that's running inside of Multipass on my Mac.  I installed Multipass and Ubuntu server 22.04 inside of it with no problems.  I then installed Ubuntu desktop using these [instructions]("https://itsfoss.com/install-gui-ubuntu-server/") from itsfoss.com and everything ran smoothly.  At first I chose lightdm as the display manager but when I got to the end of the article and didn't know why I couldn't see the desktop, I also installed GDM3.  I'm not familiar with display managers but that wasn't the problem either.


When I shell into my Multipass VM, I'm user "ubuntu".


I've started the display manager:
```

sudo service gdm3 start

```

I verify it's running:
```
sudo service --status-all | grep gdm3

```

I get the IP of the VM:
```
ip a

```

I've read that I can use Mac Finder to connect using VNC.  I've tried connecting three ways:
```
vnc://192.168.64.6
vnc://192.168.64.6:0
vnc://192.168.64.6:5900   (I read that it uses port 5900 by default)

```


When I run this VNC command I get this error:
> Connection failed to "192.168.64.6:0"
Unable to communicate with "192.168.64.6:0". Make sure the remote computer is available and the firewall is not blocking screen sharing. OK


I've read you can use Microsoft Remote Desktop so I tried connecting with it too and get a slightly different error:
> Unable to connect
We couldn't connect to the remote PC.  Make sure the PC is turned on and connected to the network, and that remote access is enabled.  Error code: 0x204.

I've been trying to research these errors but I'm new to Ubuntu Linux and haven't had any success.  I feel like I'm very close to making this work but I don't have a solid understand of each of the pieces involved and how they work together and so I'm just trying things.  I've seen many articles on how to enable remote Desktop access but they all assume that you already have access to the Ubuntu Desktop.  Can anyone tell me what I'm doing wrong?  Thanks!


Versions:
Multipass - Latest
Ubuntu server - 22.04
Ubuntu Desktop - Latest
macOS - 12.4 (Monterey)

---

### Post by TheFu on 2022-06-02
Ubuntu Desktop is Gnome4 in 22.04.  This causes problems for remote desktops. It is best to use XFCE, LXQt, Mate, or some lighter desktop with remote desktops.
Also, there are multiple methods to use a remote desktop ... but from a Mac, can't you just use remote X11 tunneling?  Do Macs support X11 (i.e. is there an X/Server on a Mac?)?  That is much easier to use than a full remote desktop.  Each program would run inside a window displayed on the Mac and appear as a native application - well, that's how it works for other Unix-based OSes.

Ubuntu Server doesn't have any desktop, no GUI.  Access to it is via ssh. You'll need to install the "ssh" package and have an ssh client on the Mac to access it.

The full remote desktop options are:
[LIST]
[*]VNC - is known for poor security and poor performance.
[*]RDP - is known for poor security and with Gnome3+, not working all that well.
[*]NX - is based on 2009 X11 code, but uses ssh for authentication and all tunneled traffic. Use x2go for this. There is an x2go server for almost any Linux (including ubuntu) and x2go clients for Windows, Macs, and Linux.  x2go is extremely network efficient, unlike the other options.  However, x2go doesn't work with Gnome3+ or KDE-Plasma DEs.
[/LIST]

I switched to x2go around 2014 for my use when traveling internationally. I've used it from the ends of the Earth, literally, from 5 different continents. Obviously, the performance is based on the bandwidth available, so I wasn't streaming 1080p videos from a hotel in Patagonia, but I was able to do typical office productivity stuff just fine - when the internet was available.  That connection provide ISDN speeds - so Kbps, not Mbps.  When I'm on the same LAN with the client and server, I don't use x2go, I use X11 forwarding.  It is integrated into my workflow.  I'm actually using this browser window on a Linux desktop with the browser running on a different computer. It is that seamless.  Watching videos works this way too, when there is sufficient bandwidth, though there are more efficient methods.

So ... for a full desktop, use x2go.  Here are some instructions: [https://wiki.x2go.org/doku.php](https://wiki.x2go.org/doku.php)  Don't forget that gnome4 and gnome3 ARE NOT SUPPORTED AND DO NOT WORK.

If you decide the inferior Gnome4 interface is still what you want (there's no accounting for taste ;) ), then [https://ubuntuhandbook.org/index.php/2022/04/ubuntu-22-04-remote-desktop-control/](https://ubuntuhandbook.org/index.php/2022/04/ubuntu-22-04-remote-desktop-control/)  There's nothing in there are Macs. Sorry.  Google did find a similar question, but no answers.  

X2go is likely the best of all the options.

---

### Post by yancek on 2022-06-03
I'd suggest that in future posts you put a link to the software (Multipass in this case) you are using so that members don't have to do an online search.  I've never heard of Multipass but an online search gave me some information.

I found the link below which purports to explain installing/using Multipass on a Mac.  Are the instructions similar to what you used? 

[https://computingforgeeks.com/run-ubuntu-virtual-machines-on-linux-macos-using-multipass/](https://computingforgeeks.com/run-ubuntu-virtual-machines-on-linux-macos-using-multipass/)

I'm curious as to why you would install Ubuntu Server (no GUI) and then install the Desktop.  Why not just start with the Desktop if you want a GUI?

---

### Post by TheFu on 2022-06-03
Multipass has been around from Canonical a few years. It is deployed as a snap package. I'd never considered that it might work on Mac.

There are lots of reasons to have a desktop AND a server. I assumed 2 systems were running.
I used to install Server to avoid the bloat and unwanted integrations that all the DEs come with.  Then I'd add the 10 GUI programs I wanted and not get stuck with the 150 others that the bloated DE includes which I'll never, ever, use.

GDM is anti-remote desktop, BTW.

---

### Post by robertfdev57 on 2022-06-03
Thank you for your thoughtful response! Performance shouldn't be a big issue for me as I only need to VM into an Ubuntu instance inside my Mac. My problem is that I don't really understand all the "pieces" that are needed and how they inter-operate, and good information about this is hard to find. If I had this understanding, this all would be easier to figure out.  All the articles I've seen are written with the assumption that you have physical access to the Ubuntu instance and can open Desktop and configure it directly. No one addresses creating a remote server, installing Desktop remotely, and then configuring it remotely and accessing it remotely.  They generally stop after the second step.  It's unfortunate that the Multipass documentation doesn't even do this.  I'll spend maybe an hour more on this and if I can't get it, I'll try Parallels Desktop.  Thanks again!

---

### Post by TheFu on 2022-06-03
> **robertfdev57 said:**
> Thank you for your thoughtful response! Performance shouldn't be a big issue for me as I only need to VM into an Ubuntu instance inside my Mac. My problem is that I don't really understand all the "pieces" that are needed and how they inter-operate, and good information about this is hard to find. If I had this understanding, this all would be easier to figure out.  All the articles I've seen are written with the assumption that you have physical access to the Ubuntu instance and can open Desktop and configure it directly. No one addresses creating a remote server, installing Desktop remotely, and then configuring it remotely and accessing it remotely.  They generally stop after the second step.  It's unfortunate that the Multipass documentation doesn't even do this.  I'll spend maybe an hour more on this and if I can't get it, I'll try Parallels Desktop.  Thanks again!

When you are new to Unix, you haven't learned the methods and much of the online talk is from Windows people who are next to clueless. They want to bring the Windows solutions to Linux rather than us the solutions which have typically worked for 30+ yrs that long-time Unix users all know. They lived it at work and in college.

It is hard to know what you don't know. That impacts everyone. I'm ignorant about Macs. Had one for 3 weeks that the company provided. Drove me crazy for the lack of control. I was unfairly thinking that MacOS was Unix, so I'd be happy.  Deep underneath that may be true, but the GUI is so limiting. Some standard things worked and worked well.  But there were times I wanted to pick up the machine and smash it against the wall. It was so very frustrating.  
I wasn't being fair. We always say to Windows people that "Linux isn't Windows".  I reminded myself that MacOS isn't Linux and found my "happy place" long enough to see some beautiful things in the GUI and why people could love it. The consistency alone is amazing.  OTOH, the way that Apple insists on using apple-if-fied names for standard protocols was really frustrating to me.

Remote access has been part of X11 for 40+ yrs. It is assumed.  But a Mac doesn't have an X/Server (by default), so the normal method used by millions of Unix people world-wide gets translated in to VNC/RDP, which are inferior for usability in so many ways.  

Before computers were cheap, we used Xterminals (a hardware device) ... which used the xdmcp protocol to provide a login page from the xterminal hardware on our desks that connected to the shared Unix server 50 miles away in the data center that the 2000 employees all shared.  [https://wiki.ubuntu.com/xdmcp](https://wiki.ubuntu.com/xdmcp)  Ubuntu can use this.

After computers became cheap, we'd run an X/Server on the platform at our desk and remote into the remote server running the X/Client application there with the DISPLAY environment variable set to our local X/Server DISPLAY (that's usually an {IP}:0), and the program would appear on the local monitor like any other.  When ssh became available, it included an X11Forward option which creates an ssh tunnel for X protocol traffic and automatically sets the DISPLAY correctly.  I've been using that to run Firefox, Thunderbird, and many other programs since the mid-1990s.

This is how it works:
```
$ ssh -X {remote-host} {command} {command options}
```

So, a real-world example that runs thunderbird on my normal desktop in a private cloud:
```
$ more ~/bin/thunderbird.sh 
#!/bin/bash
FJ_OPTS="--dns=172.22.22.80 --rlimit-as=4700000000 "
TB_OPTS="-no-remote "
# limit RAM VSS to 4G
PID=$(ssh -X  regulus /usr/bin/firejail $FJ_OPTS /usr/bin/thunderbird $TB_OPTS $@ & )
exit;
```

Typically, people who use a desktop environment aren't the admins running the systems. They have a local install. 

But if a normal desktop OS was installed into Multipass, I'd be surprised if there wasn't a menu with the installed OSes to be clicked to start and after starting that the desktop screen wouldn't just show up. This is how Virtualbox, VMware Workstation/Player, and virt-manager work for desktop OSes installed onto a desktop system.  I've never gotten Multipass working ... something about the snap package doesn't work on my systems. I get errors from snaps that aren't worth changing my entire LAN setup to fix just to support snaps.  Plus, kvm-qemu with virt-manager and virt-viewer are the state of the art for virtual machines - both desktops and inside an enterprise.  The virt-manager might be replaced by a different tool (perhaps oVirt) when there are thousands of VMs to be managed, but the underlying stuff is all the same.

Of course, none of this is MacOS specific.

I wrote an article about 10 yrs ago describing remote desktop and remove GUI access for Unix systems.  
[https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)
They are all built around using X/Windows, so to any Mac user, I think step 1 is to install an X/Server on your Mac.  Then the world opens up.  Virtual machines don't really matter, since all the protocols are network-based.

---

### Post by robertfdev57 on 2022-06-04
You're right about providing the link.  On the other hand, since Multipass is a Canonical product, I just assumed that people on this board would know what it was.

---

### Post by robertfdev57 on 2022-06-04
Thank you Fu.  I appreciate your taking the time to provide a detailed answer.  If I can get this working, I'll follow up here for the benefit of others who run into the same problem in the future.

---

### Post by deadflowr on 2022-06-04
Here: [https://discourse.ubuntu.com/t/how-to-set-up-a-graphical-interface/28719]("https://discourse.ubuntu.com/t/how-to-set-up-a-graphical-interface/28719")
This is from the developers themselves.

---

### Post by HermanAB on 2022-06-04
In brief: 
You need to use Xorg on Linux (Xfce with Xorg, not Wayland with Gnome) and you need to install an X server on the Mac (Xquartz).  

Then of course, you have to run Xquartz before you try to connect to the remote machine.

---

