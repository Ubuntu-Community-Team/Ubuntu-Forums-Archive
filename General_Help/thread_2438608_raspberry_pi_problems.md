---
title: "raspberry pi problems"
date: 2020-03-14
forum: General Help
---

### Post by hmiersch on 2020-03-14
the other day i installed ubuntu 19.10 and the desktop on my raspberry pi. so far so good. but when i go into settings, i can not configure the network. i only see the boxes for VPN and proxy, but not the one for the wired network. did something go FUBAR during installation? is it supposed to be this way?    also, when i go into settings -> devices -> screen display, it only gives me one weird resolution, 1824 by 984, or something like that. what's going on there?   the last problem has probably more to do with hardware than software, but the Pi only shows me a signal when i connect it directly to my TV, but not when i connect it to the HDMI switch. problem is, my TV only has one HDMI in, which is why i bought the switch in the first place. and why the XXXX do my blank lines keep disappearing?

---

### Post by DuckHook on 2020-03-14
In no particular order:

KVM switches are notoriously wonky in Linux. They are built and tested to work with Windows and, to a lesser extent, with Apple. Linux is at best an afterthought and more often not even that. It is not surprising that you get no signal. You can try defining a Xorg.conf file but it has been ages since I've had to do anything like that, so can't be of much help.

Your resolution is likely the result of your TV settings. Many TVs are set up to overscan which cuts off some pixels from all sides. It's a legacy of the way broadcast TV used to work in the CRT days. To fix:

[list=1]
[*]Make sure your TV is set to PC mode/computer mode. Some manufacturers call it dot for dot, or something similar.
[*]Under Settings &#8594; Devices &#8594; Screen Display, make sure *Adjust for TV* is turned off.
[/list]
The Ubuntu image for the rPi does not have Network Manager installed by default. To install:```
sudo apt install network-manager
```

---

### Post by hmiersch on 2020-03-14
adjust for TV? i just checked on my PC (also running 19.10), and i can't find that option. hmm...  can i run that sudo command via ssh when i boot the Pi headless? gonna try it...

---

### Post by hmiersch on 2020-03-15
well, looks like i can NOT ssh into it when i boot it headless :-(  ok, shut down the PC and plug in the Pi :-(

---

### Post by hmiersch on 2020-03-15
I ran that sudo command, and it told me network manager is already installed. But in settings I still can't configure the network. Any ideas? Do I need to configure it? How do I do that?

---

### Post by DuckHook on 2020-03-15
> **hmiersch said:**
> I ran that sudo command, and it told me network manager is already installed. But in settings I still can't configure the network. Any ideas?
It could be this old problem: [https://askubuntu.com/questions/904545/networkmanager-doesnt-show-ethernet-connection](https://askubuntu.com/questions/904545/networkmanager-doesnt-show-ethernet-connection)

---

### Post by hmiersch on 2020-03-15
here's the next problem. i tried to edit networkmanager.conf but vim keeps telling me the file is read-only. so i tried to change its permissions with chmod u+w networkmanager.conf, but that didnt work, not even when i used sudo. even after a restart vim still tells me the file is read-only. what am i doing wrong? should i try another editor? which one?     

Update: I tried pico instead of vim, and that worked. I configured the Ethernet correctly. Now I'm trying to find out why I still can't get online...

---

### Post by hmiersch on 2020-03-15
ok, i have no idea whats going on. i can finally configure the ethernet on the pi, which i did. but the problem is that i can't get to the internet. after adding some rules to ufw, i can ssh into the other computers on my LAN, i can access the pihole user interface from another computer, i can manage my network hardware. and i can get on the internet using the other computers. but i can not get the pi on the internet. i cant go to youtube or any other website, i cant update the software, i cant sync the clock, i cant install software, i cant do anything on the internet, and i cant even find out why. i've allowed outbound connections to ports 22 (ssh), 53 (DNS), 80 (http), 123 (ntp), 443 (https) and 8443 (https for network management)

 any ideas, anyone?

---

### Post by DuckHook on 2020-03-15
Let's hope some networking guru steps in here (which I'm not).

To help us help you, please provide a more complete context behind what you are trying to do. Your info is being posted in bits and pieces. What are you trying to do with the rPi? Assembling from among your various posts, so far what we have is:

[list]
[*]You are on 19.10.
[*]You are trying to use it as a pi-hole.
[*]You activated UFW
[*]You've opened up some outbound ports (what about inbound?).
[*]You are unfamiliar with VIM (it's a modal editor that is ornery for us ordinary folks. Use nano or pico instead).
[*]Something is stopping you from accessing the Internet from the rPi.
[/list]
Please flesh out further this skeletal description.

[list=1]
[*]Do you have a GUI desktop environment installed on top of the rPi image? A DE doesn't play nice on the rPi. If you want a DE, I highly recommend sticking with Raspbian.
[*]Do you notice any messages when attempts fail?
[*]What do your logs tell you, especially dmesg, syslog and auth.log?
[/list]
As noted, my knowledge of networking is limited. Hopefully a networking expert sees this.

---

### Post by TheFu on 2020-03-16
i know ZERO about Ubuntu on rPi.  Lots of experience w/ raspbian and a few other specialized media distros.  Many will have specific configs to about writing too much to the SD storage. This will help the storage to last longer, but it makes for a different setup than normal x86 linuxen.

i thought networking on rPi systems used conman from intel.  iMHO, network-manager is an abomination.

When editing any system files on any linux, use **sudoedit**.

A pi-hole is a specialized, headless, rPi distro. Probably want to use dd to put the image onto the SD storage, then use the web interface for any local configuration.

Almost all computers outside corporate installs won't block outbound connections.  This means that opening outbound firewall rules isn't needed.  if you want to ssh into the rPi, then you need to setup an inbound rule to allow that, but only if the firewall is enabled, which is not the default for Ubuntu.  in short, don't screw with the firewall until you have everything working.

Also - a pi-hole is meant to be a single-purpose device, not anything else.

---

