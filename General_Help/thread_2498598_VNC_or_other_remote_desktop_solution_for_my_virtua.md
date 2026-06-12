---
title: "VNC or other remote desktop solution for my virtual Ubuntu machine"
date: 2024-06-21
forum: General Help
---

### Post by zeezam on 2024-06-21
I'm running Ubuntu 22.04.4 LTS as a Hyper-V guest on my Windows 11 desktop.

Now I want to have some other remote desktop than virtual machine Connection (it's a bit laggy).

First I wanted to configure and run x11vnc but there are maybe other better solutions?

Checked some guides and manual (also searched this forum) but I'm getting in trouble when mix in the .Xauthority, the x11vnc.pass file and -display :1.

I have checked and display is :1.

I have /lib/systemd/system/x11vnc.service with this
```

/etc/x11vnc.pass[Unit]
Description=x11vnc service
After=display-manager.service network.target syslog.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -display :1
ExecStop=/usr/bin/killall x11vnc

[Install]
WantedBy=multi-user.target

```

With just "ExecStart=/usr/bin/x11vnc" I can get the service to run but not possible to connect with RealVNC for example.
Earlier it went fine connecting remote without .Xauthority and x11vnc.pass. 

Any ideas/tips?

---

### Post by TheFu on 2024-06-21
x2go is what you want, but there are specific requirements.
a) No gnome or KDE. Use a DE like Mate, XFCE, or something light.
b) No Wayland.  Use Xorg.
c) Setup ssh between the client and server first. All NX remote desktop solutions go through an ssh tunnel, so this needs to be working first.

That should be enough to get you started.

I've never used nor seen Hyper-V anywhere.
VNC and RDP network security are really poor.  x2go doesn't require someone to be logged in locally and walk away. GUi sessions are virtual and there aren't any magic limits for the number of concurrent sessions allowed, beyond what the hardware can support (typically RAM).  I've seen small teams - say 8 people - all work together on the same small desktop as an x2go server.  With RAM these days, 20+ sessions wouldn't be a problem.

---

### Post by zeezam on 2024-06-21
> **TheFu said:**
> x2go is what you want, but there are specific requirements.
a) No gnome or KDE. Use a DE like Mate, XFCE, or something light.
b) No Wayland.  Use Xorg.
c) Setup ssh between the client and server first. All NX remote desktop solutions go through an ssh tunnel, so this needs to be working first.

That should be enough to get you started.

I've never used nor seen Hyper-V anywhere.
VNC and RDP network security are really poor.  x2go doesn't require someone to be logged in locally and walk away. GUi sessions are virtual and there aren't any magic limits for the number of concurrent sessions allowed, beyond what the hardware can support (typically RAM).  I've seen small teams - say 8 people - all work together on the same small desktop as an x2go server.  With RAM these days, 20+ sessions wouldn't be a problem.

I'm using Gnome (default) - isn't that possible? :|

Ssh is working fine, I use that one meanwhile.

I thought it was easy to use Hyper-V because I got it with windows 11. Maybe will install a standalone Ubuntu machine later.
[https://ubuntu.com/server/docs/how-to-set-up-ubuntu-on-hyper-v](https://ubuntu.com/server/docs/how-to-set-up-ubuntu-on-hyper-v)

---

### Post by TheFu on 2024-06-21
I was pretty clear about the requirements. Either believe me or not.   Gnome3 and later decided to require 3D GPUs.  Remote desktops don't have 3D GPUs.  Gnome doesn't care about corporate users or people running remotely in mixed environments.   [https://askubuntu.com/questions/958986/x2go-compatibility-problems](https://askubuntu.com/questions/958986/x2go-compatibility-problems) 

I understand that Wayland and Gnome4 if the client and server are both 24.04 can work.  I've never used it because Wayland breaks too many of my other workflows to be considered.

---

### Post by zeezam on 2024-06-21
Ok. Your solution is certainly good but I also want rather go with a simpler solution if possible. Edit: Also something that works by default.

RDP is out of the scoop?
[https://phoenixnap.com/kb/ubuntu-remote-desktop-from-windows](https://phoenixnap.com/kb/ubuntu-remote-desktop-from-windows)

Is it not enough secure with a home router or what do you mean?

---

### Post by currentshaft on 2024-06-21
I wouldn't really worry about VNC/RDP security on a private network where all the devices are owned by you, though tunneling over SSH shouldn't hurt performance either.

Forwarding X is notoriously slow. What programs are you trying to use that way?

---

### Post by TheFu on 2024-06-21
> **currentshaft said:**
> I wouldn't really worry about VNC/RDP security on a private network where all the devices are owned by you, though tunneling over SSH shouldn't hurt performance either.

Forwarding X is notoriously slow. What programs are you trying to use that way?

On the same LAN, I use X11 forwarding constantly, between systems.  This browser window is running on a different system on the LAN, for example.  That's very different than using the bloat of a full remote desktop.  On the same LAN, running an application on a different system is pretty trivial.

```
$ ssh -X user@remote-hostname  command-to-be-run options-for-the-command
```

A slightly more complex example, for how I run Thunderbird on a remote system (on the LAN), 
```
#!/bin/bash
FJ_OPTS="--dns=172.22.22.81 --rlimit-as=4700000000 "
TB_OPTS="-no-remote "

# limit RAM VSS to 4.7G
/usr/bin/ssh -X  deneb /usr/bin/firejail $FJ_OPTS /usr/bin/thunderbird $TB_OPTS $@ & 

```

Deneb is the remote system to run the firejail + thunderbird on.  The username on both systems is the same, so it isn't required.  Thunderbird doesn't like to be run remotely by default, hence the -no-remote option. This is a Mozilla thing.  Also, a few Mozilla programs like to use Mozilla's DNS, not my internal DNS, so I have firejail force the use of mine.   I also prevent thunderbird from snagging more and more and more RAM that will never be used.  Mozilla programs have this problem - especially Firefox.  Once a firefox instance had allocated 68GB on a system that only had 32GB of RAM and 4G of swap, so clearly there's an issue with Mozilla AND with Linux memory allocations.  In theory, the OS should never allow allocations beyond what is actually available, but for a 80-90% performance improvement, the kernel malloc() function never checks whether requested RAM is available. It is a trade off that seldom matters, but sometimes it does.  

The basic command is still the same:
```
ssh -X remote-system command
```

---

### Post by zeezam on 2024-06-21
Works good with rdp. Not slow. A little low resolution. It's max in windows rdp client.

[ATTACH=CONFIG]293897[/ATTACH]

Edit: This works for the resolution:

```

Open Terminal on your Ubuntu VM.

Enter sudo nano /etc/default/grub.

Find the line GRUB_CMDLINE_LINUX_DEFAULT and modify it with the resolution you want, for example: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=hyperv_fb:1920x1080".

Save and exit the editor (in nano, it’s Ctrl+X, then Y to confirm changes, and Enter to save).

Update GRUB with sudo update-grub.

Reboot your VM.

```

Edit: One strange thing - I need to sign in virtual machine one time before I can sign in to RDP, don't know why. Is there any logs somewhere?

Edit: This seems to help for the hyper-v graphical performance:

```
sudo nano /etc/modprobe.d/blacklist.conf
Add the line: blacklist hyperv_fb
```

```
sudo apt-get install linux-virtual linux-cloud-tools-common linux-image-virtual linux-headers-virtual
```

---

