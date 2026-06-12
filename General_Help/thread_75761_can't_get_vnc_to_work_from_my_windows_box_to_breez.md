---
title: "can't get vnc to work from my windows box to breezy"
date: 2005-10-14
forum: General Help
---

### Post by minktoast on 2005-10-14
I have just installed Breezy.

I have enabled Remote Desktop and set it to allow people to control desktop and require a password.  I leave Ubuntu logged in at a Gnome desktop.

I then try to connect across my LAN from my Windows box with VNC (by IP address), but I get connection refused.  (VNC works fine on my LAN - Windows to Windows)

Any ideas on what I need to do to get this to work?  Many TIA from Ubuntu newbie.

---

### Post by dbott67 on 2005-10-14
Just a few questions:

1. Do you have firewall enabled on your Ubuntu box?
2. What is the IP address of your Ubuntu box?  What is the IP of your Windows box?  Can you ping Ubuntu from Windows & vice-versa?
3. Do other services work (i.e. can you access a Windows share from Ubuntu,  can you VNC from Ubuntu to Windows, etc.)?

-Dave

---

### Post by mbeach on 2005-10-14
I had a similar issue.  In my environment, the default gateway plays a huge role and if I use DHCP I'm very limited as to what ports I can use.  If I use a static IP and hardcode the gateway to our more open gateway, everything works fine.  Our DHCP supplied gateway is very strict with it's filters for security reasons.  I'd suggest ensuring your Ubuntu box is using the same gateway as working win-win vnc-able machines.  [System | Administrator | Networking | Ethernet connection | Properties ]

---

### Post by minktoast on 2005-10-15
Thanks for you resposnes.

In answer to your questions:

1. I don't _think_ I have a Firewall enabled on Breezy - this is a new clean default installation.  I haven't changed anything - just installed from CD and started using.

2. Breezy IP is 192.168.1.5  Windows IP is 192.168.1.2  I can ping both ways.  I am using DHCP from my router.

3. I can see Windows shares from Ubuntu.  Using tsclient on Ubuntu I can VNC to my Winodws machine.

4. I am using the same router / gateway (USR 9106) that works with VNC in Windows.

My problem remains, if I open VNC Viewer on my Windows machine and enter: '192.168.1.5' I get 'uanble to connect to remote host: Connection refused (10061)'

Any ideas?  Is Breezy running a firewall by default?  Sorry if I'm missing something obvious but I am very much a newbie.

---

### Post by dbott67 on 2005-10-15
Here's a few more things to check:

1. From a command prompt on the Ubuntu box type:
```
netstat -l
``` This will provide a list of listening ports on your system. If VNC server is running, you should see something listening on port 5900. If not, then for some reason VNC server is not running.

2. Double-check your settings in Remote Desktop. Make sure that under the 'Security' section that the 'Ask you for confirmation' is unchecked.

I've attached a screenshot of my desktop showing the listening port and the box to be unchecked.

-Dave

---

### Post by minktoast on 2005-10-15
Thanks Dave - "netsat -l" does NOT show my machine listening on Port 5900.

My Remote Desktop preferences were OK.

Do you know how I start VNC server manually and how to make it autostart on boot-up? (A quick search didn't shed any light on this.)

I wonder why it isn't running on my system - the only non-default thing I did when installing Breezy was to type "linux noapic" to get the installer to run on the laptop.  Might this have affected things.

Thanks again for your help.

---

### Post by dbott67 on 2005-10-15
Here's my WinXP box (outside D-Link Router) connected to my Ubuntu box (inside D-Link Router).

I setup port-forwarding on TCP 5900 to re-direct to the internal NAT address of my Ubuntu box (in this case 192.168.0.102).

-Dave

---

### Post by dbott67 on 2005-10-15
The vncserver should startup automatically once you check those boxes in Remote Desktop.  You can always type **/usr/lib/vino/vino-server** at the command line (the actual line as outputted by ps -aux is **/usr/lib/vino/vino-server --oaf-activate-iid=OAFII**).

Can you post the output of **netstat -l** for me, as well as [B]ps -aux?

[/B]Thanks,
Dave

---

### Post by minktoast on 2005-10-15
OK - I've attached the output from the commands suggested.

Also, if I type, '/usr/lib/vino/vino-server --oaf-activate-iid=OAFII' or '/usr/lib/vino/vino-server' I get:

'Bad Segmentation'.

Hope this helps - I'm out of my depth now! Thanks for your help.

---

### Post by dbott67 on 2005-10-15
Well, about all I can recommend is that you try a complete removal & reinstallation from Synaptic.

1. Open Synaptic, search for 'vino' and then select for complete removal.
2. Click APPLY and after it's complete, reboot the computer.
3. Go back into Synaptic & double-check your repositories to make sure that you have the extra repos selected. Also disable any 'backports' or other unofficial Ubuntu repos. Your sources.list file should look like this:
```

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
``` 4. Now, re-install 'vino'

Let me know if it works.

-Dave

---

### Post by minktoast on 2005-10-15
Didn't work.  Am giving up for now - will try again in about a week when I have some more spare time.  Thanks for all your help.  Will report back here if I ever get it working.

---

### Post by Dongjoon Hyun on 2005-10-22
Would you try to use "192.168.1.5:0" instead of "192.168.1.5"?

I have connected from Windows XP to Ubuntu via VNC.

But, I can connect  only when I log on in Ubuntu.

---

### Post by staticsage on 2005-10-24
Try using a different VNC server.

I recommend the package vnc4server to share virtual desktops:

sudo apt-get vnc4server

If you want to share a physical display, try using x11vnc

sudo apt-get x11vnc



Personally, I run vnc4server because I run a headless machine. It displays a virtual desktop, and clipboard sharing works seemlessly (took me so long to find a package that supported that without tinkering). To have it autostart, I add a line to the /etc/init.d/bootmisc.sh file (probably not the most elegant way, but it works).

---

### Post by sb73542 on 2006-03-03
The default encoding on the Windows client has to be set to "Raw", not "tight".  The default Ubuntu VNC server doesn't serve out "tight" encoding.

---

### Post by frio on 2006-04-05
I agree with **staticsage** about installing vnc4server on you Ubuntu box. I had a similar problem until I did this. What version of vnc are your Win boxes using? I believe ubuntu uses v3.3 vnc from the base install.

---

