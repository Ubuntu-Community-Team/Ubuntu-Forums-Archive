---
title: "Getting help for Ubuntu Core?"
date: 2024-09-16
forum: General Help
---

### Post by turrican32 on 2024-09-16
Hey there, I'm experiencing a very annoying issue with Ubuntu Core, but I can't see it mentioned here (unless I'm missing something very obvious, that is)

So where exactly do I ask for help?

Sorry if the question has been answered a few thousand times, Google isn't helping either unfortunately...

---

### Post by ian-weisser on 2024-09-16
All official Ubuntu support venues (including this one) handle all currently-supported releases of Ubuntu.

While we may not have too may Core users here, we will still do our best to help.

Describe the version of Ubuntu Core and your issue.

---

### Post by turrican32 on 2024-09-16
Thank you so much for the quick reply, I just wanted to make sure I wasn't going to be way much off-topic, or something like that.

I'm currently evaluating Ubuntu Core for a kiosk-like use case; basically, the one and only thing that this PC is going to do is launching a remote desktop.

Unfortunately, I haven't been able to run remmina (tried both regular and edge release channel) to achieve my goal until now, I only get a blank grey ubuntu frame screen.

What I did:

- downloaded and installed a pre-built Ubuntu Core 24 x86 image from the official website (specifically, [this one]("https://cdimage.ubuntu.com/ubuntu-core/24/stable/current/ubuntu-core-24-amd64.img.xz")), linking my Ubuntu One account, ssh keys, etc.
- tried and successfully deployed the docs-suggested Internet Web Kiosk so that I was at least sure the basics were ok (had to fiddle a bit with this one because I tried with a Proxmox-based virtualization, that didn't work so I had to switch to a local, vmware-based VM... not Ubuntu's fault by the way, just to give the whole picture)
- removed the aforementioned web browser and installed remmina via snap install (as I said, I tried both the default and the edge versions), set the "server" option to the IP I need to connect to, but nothing happens

All I get is a blank (grey) screen, plus the following messages when I issue the 

snap logs remmina

command:

> 2024-09-16T07:20:13Z systemd[1]: Started snap.remmina.ssh-agent.service - Service for snap application remmina.ssh-agent.
2024-09-16T07:20:13Z remmina.ssh-agent[55772]: SSH_AUTH_SOCK=/var/snap/remmina/6672/ssh-agent.socket; export SSH_AUTH_SOCK;
2024-09-16T07:20:13Z remmina.ssh-agent[55772]: echo Agent pid 55772;
2024-09-16T07:26:16Z systemd[1]: Stopping snap.remmina.ssh-agent.service - Service for snap application remmina.ssh-agent...
2024-09-16T07:26:16Z systemd[1]: snap.remmina.ssh-agent.service: Main process exited, code=exited, status=2/INVALIDARGUMENT
2024-09-16T07:26:16Z systemd[1]: snap.remmina.ssh-agent.service: Failed with result 'exit-code'.
2024-09-16T07:26:16Z systemd[1]: Stopped snap.remmina.ssh-agent.service - Service for snap application remmina.ssh-agent.
2024-09-16T07:26:41Z systemd[1]: Started snap.remmina.ssh-agent.service - Service for snap application remmina.ssh-agent.
2024-09-16T07:26:41Z remmina.ssh-agent[57435]: SSH_AUTH_SOCK=/var/snap/remmina/6672/ssh-agent.socket; export SSH_AUTH_SOCK;
2024-09-16T07:26:41Z remmina.ssh-agent[57435]: echo Agent pid 57435;

Any suggestions?

Feel free to ask any further info that I may have unintentionally omitted.

---

### Post by Holger_Gehrke on 2024-09-17
What kind of connection are you trying to establish ? remmina can work with multiple protocols (according to 'apt show remmina': "Currently RDP, VNC, SPICE, WWW, X2Go, EXEC and SSH are supported."). At least with vnc what you're describing is normal if you haven't set up the session on the server side (vnc will just start a new X session with no programs - not even a window manager - running; meaning you get a grey screen and a mouse cursor shaped like a diagonal crosshair).

Holger

---

### Post by turrican32 on 2024-09-17
I'm trying to setup an RDP connection to a Windows 10 machine.  

I am able to connect via Windows own Remote Desktop application so I believe everything is correctly setup on the receiver end.  

I also have added a 

snap set server="rdp://username@ip_address" 

option to the Ubuntu Core configuration, but I'm not sure this is enough (nor if it is correct!)

---

### Post by ian-weisser on 2024-09-17
Ubuntu Core is not currently designed to host a desktop GUI.
It lacks the entire graphical stack: Display Manager, compositor, window manager, etc. Ubuntu Core has none of them.

The kiosk snap has just enough of that stack to run the web browser, but nothing else.

The Reminna snap is intended for use with an existing Ubuntu Desktop system. That snap does not contain the entire missing GUI stack.

Your design is clever, but it won't work with the current releases of Ubuntu Core.

There is in development, slowly, for several years, a desktop version of Ubuntu Core. When released (no known proposed date), the Reminna snap should work with it.

---

### Post by turrican32 on 2024-09-18
Oh now I see why this isn't working, thanks for the explanation!

Unfortunately I have a relatively little understanding of the whole "under the hood" (for a lack of a better working) Ubuntu/Linux architecture, that's why I mistakenly thought that as web snap was working, surely the RDP client would too. I found out I was wrong the hard way.

Any suggestion the achieve the desired goal? (i.e. a mostly immutable configuration that can run a Windows remote desktop client)

Switching distro isn't an issue by the way, if I need to (and I guess I really do? I mean I assume you just can't add the missing components and call it a day, otherwise you would have told me)

---

### Post by grahammechanical on 2024-09-18
Canonical is working on a version of Ubuntu Core with a desktop environment. I am downloading the ISO image right now. Consider it experimental.

[https://cdimage.ubuntu.com/experimental/ubuntu-core-desktop/24/stable/20240209/](https://cdimage.ubuntu.com/experimental/ubuntu-core-desktop/24/stable/20240209/)

[https://discourse.ubuntu.com/t/ubuntu-core-desktop-deep-dive/37740](https://discourse.ubuntu.com/t/ubuntu-core-desktop-deep-dive/37740)

Regards

---

### Post by grahammechanical on 2024-09-18
I downloaded the Ubuntu Core Desktop ISO image and burnt it to USB stick. Not happy with the result. The Try Ubuntu session loaded to a purple screen with a white cursor and got no further. Loading the session in safe mode did not even get to the purple screen. It seemed to be detecting the hardware and then stopped at this message:

> finished casper-md5check.service - casper -md5check verify live iso checksum 

CTRL + ALT + DEL shuts it down with a remove medium and press ENTER message.

So, this Ubuntu Core Desktop ISO image is truly an experimental project at this time. I will see how it develops over time.

Regards

---

### Post by 1fallen on 2024-09-18
> **grahammechanical said:**
> I downloaded the Ubuntu Core Desktop ISO image and burnt it to USB stick. Not happy with the result. The Try Ubuntu session loaded to a purple screen with a white cursor and got no further. Loading the session in safe mode did not even get to the purple screen. It seemed to be detecting the hardware and then stopped at this message:


I was going to warn you first, but then I hoped just maybe you would have had a better outcome.

---

### Post by 1fallen on 2024-09-18
I finally got it. Here is how it lays  out 
```
Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 6.5.0-44-generic x86_64)
 * Ubuntu Core:     https://www.ubuntu.com/core
 * Community:       https://forum.snapcraft.io
 * Snaps:           https://snapcraft.io

This Ubuntu Core 22 machine is a tiny, transactional edition of Ubuntu,
designed for appliances, firmware and fixed-function VMs.

If all the software you care about is available as snaps, you are in
the right place. If not, you will be more comfortable with classic
deb-based Ubuntu Server or Desktop, where you can mix snaps with
traditional debs. It's a brave new world here in Ubuntu Core!

Please see 'snap --help' for app installation and updates.
Last login: Wed Sep 18 20:47:13 2024 from 127.0.0.1



```
```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
[sudo] password for me: 
NAME    FSTYPE    SIZE MOUNTPOINT                                    LABEL
loop0   squashf 516.4M /writable/system-data/snap/core22-desktop/267 
loop1   squashf   1.6M /writable/system-data/snap/pc-desktop/23      
loop2   squashf 282.9M /writable/system-data/snap/pc-kernel/1881     
loop3   squashf   1.5M /writable/system-data/snap/avahi/327          
loop4   squashf     4K /writable/system-data/snap/bare/5             
loop5   squashf   1.3M /writable/system-data/snap/bluez/356          
loop6   squashf  55.7M /writable/system-data/snap/core18/2829        
loop7   squashf    64M /writable/system-data/snap/core20/2379        
loop8   squashf  74.1M /writable/system-data/snap/core22/1033        
loop9   squashf  66.2M /writable/system-data/snap/core24/490         
loop10  squashf  66.5M /writable/system-data/snap/cups/1024          
loop11  squashf 164.8M /writable/system-data/snap/gnome-3-28-1804/19 
loop12  squashf   497M /writable/system-data/snap/gnome-42-2204/141  
loop13  squashf  91.7M /writable/system-data/snap/gtk-common-themes/ 
loop14  squashf   4.1M /writable/system-data/snap/ipp-usb/101        
loop15  squashf 152.1M /writable/system-data/snap/lxd/26200          
loop16  squashf   4.6M /writable/system-data/snap/network-manager/87 
loop17  squashf 280.7M /writable/system-data/snap/pc-kernel/1570     
loop18  squashf  10.5M /writable/system-data/snap/snap-store/1046    
loop19  squashf  40.6M /writable/system-data/snap/snapd/21018        
loop20  squashf  37.2M /writable/system-data/snap/snapd/23021        
loop21  squashf   476K /writable/system-data/snap/snapd-desktop-inte 
loop22  squashf 134.3M /writable/system-data/snap/surfshark/42       
loop23  squashf  20.9M /writable/system-data/snap/ubuntu-core-deskto 
loop24  squashf    12K /writable/system-data/snap/ubuntu-desktop-ses 
loop25  squashf  74.3M /writable/system-data/snap/core22/1612        
loop26  squashf   4.6M /writable/system-data/snap/network-manager/90 
loop27  squashf   1.3M /writable/system-data/snap/bluez/381          
loop28  squashf   1.1M /writable/system-data/snap/avahi/615          
loop29  squashf   560K /writable/system-data/snap/snapd-desktop-inte 
loop30  squashf  67.8M /writable/system-data/snap/cups/1058          
loop31  squashf   7.4M /writable/system-data/snap/gedit/684          
loop32  squashf 104.1M /writable/system-data/snap/lxd/30130          
loop33  squashf   173M /writable/system-data/snap/brave/438          
loop34  squashf 505.1M /writable/system-data/snap/gnome-42-2204/176  
loop35  squashf 271.4M /writable/system-data/snap/firefox/4955       
loop36  squashf   5.2M /writable/system-data/snap/eog/728            
sda              29.3G                                               
&#9500;&#9472;sda1              1M                                               
&#9500;&#9472;sda2  vfat      3.4G /writable/system-data/var/lib/snapd/seed      ubuntu-seed
&#9500;&#9472;sda3  ext4      750M /run/mnt/ubuntu-boot                          ubuntu-boot
&#9500;&#9472;sda4  ext4       32M /writable/system-data/var/lib/snapd/save      ubuntu-save
&#9492;&#9472;sda5  ext4     25.1G /writable                                     ubuntu-data

```
A couple of snapshots to view.

---

### Post by turrican32 on 2024-09-19
Thank you so much everyone, I'll give that a try too.

Meantime, i hope this desktop version can reach stable status as soon as possible, that would spare me quite a few headaches. ^__^

---

### Post by 1fallen on 2024-09-19
Just to help if needed I used an .img install found here: [https://cdimage.ubuntu.com/experimental/ubuntu-core-desktop/24/stable/current/ubuntu-core-desktop-24-amd64.img.xz](https://cdimage.ubuntu.com/experimental/ubuntu-core-desktop/24/stable/current/ubuntu-core-desktop-24-amd64.img.xz)
Extracted the single .img file, then the fun part.
I had a blank 32Gig Drive so I burned that to that Drive, booted to it and let it install. Just be patient for the installer to finish.

There will be no GUI installer shown it takes care of that on it's own. But it will fill the entire drive. (Heads Up)

---

### Post by turrican32 on 2024-09-19
Yeah the .iso didn't work (got a blank screen) so I tried and successfully installed the usual .img file via Disk Writer.

I'm currently trying to finally have my user autologin (despite setting the option during the OS Setup phase, I still need to enter the password - this needs to be fixed) and let Remmina automatically run, but I'd say I'm in a definitely better state compared to two days ago. :-)

---

### Post by TheFu on 2024-09-19
If I were trying to do this, I'd start with TinyCore Linux (the version that includes Xorg) and add just the RDP client I wanted.  Bet all that would fit in less than 64MB (yes, MB).

---

### Post by turrican32 on 2024-09-20
Hmm, 64MB sounds intriguing to say the least (I'd happily take the least complex configuration anytime!), I'll give that a try too, thanks!

---

