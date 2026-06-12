---
title: "start up app"
date: 2020-11-11
forum: General Help
---

### Post by Old Jimma on 2020-11-11
Hi Community:

I have an app that I want to start as  soon as the computer boots.

I want to use the start-up app to add this app to the others that start up on booting.

THe Ubuntu start-up app requres the command for start up apps.

How do i find that command... and the path to that command?

Thanks,
Old

---

### Post by SeijiSensei on 2020-11-11
If you want the process to run with root privileges, put the command in /etc/rc.local.  If it doesn't exist, create it yourself.

---

### Post by TheFu on 2020-11-11
Starting an app at boot is different from starting an app just after login.

GUI programs have to wait to be started until after a user logs in.  Most "Desktop Guides" have a section on startup applications.

CLI programs can be started provided any dependencies are already available. It makes little sense to start a program that needs a network connection before networking is up. This is a little harder, since the rc.local has been deprecated.  Also, most programs need a little environment that has to be manually setup before they will run.  In a terminal, type 'env' and see all those variables that are set?  A few of those are necessary for certain programs to work - not all, just a few.  If you run 'env' from the rc.local (after enabling that) and write the output to a file, you can compare that file with the output from your terminal. Notice the huge differences?  This is why some programs don't work.

---

### Post by Old Jimma on 2020-11-11
Hi SeijiSensei and TheFu,

Thanks for your informative replies!!!

Old JImma from the Old Country

---

### Post by #&amp;thj^% on 2020-11-11
First please note this may provide a lot of convenience, it is important to remember not to overuse this feature. Users might face problems when a large number of tasks are provided or selected to be automated. The main problem this leads to is slowing down your system at startup. Hence, it is very important for the user to NOT over utilise this functionality and only automate the most required or used tasks.

Now you asked this.
> THe Ubuntu start-up app requres the command for start up apps.

How do i find that command... and the path to that command?
This is very DE dependant, EG: Gnome uses (gnome-session-properties)  Mate uses (mate-session-properties) XFCE4 uses (xfce4-session-settings) KDE/Plasma is a bit more complex, One excellent feature that KDE Plasma 5 has above other Linux desktop environments is that the Autostart GUI tool lets users automatically run Bash scripts during login.

To do this, make your way to the “Autostart” section of System Settings ( System Settings > Workspace > Startup and Shutdown  > Autostart). Then, in the Autostart section, find the “Add Script” button and click on it with the mouse.
Just Added Info hopefully useful. ;)

---

### Post by Old Jimma on 2020-11-11
Hi All:

thanks to all who provided replies. I am grateful for your thought and effort.

Can I tell you what worked for me? I don't mean any disrespect by my reply.... just to tell you my experience.

I found the executable in /opt/piavpn/bin  (piavpn is the software "name".... a vpn service I use)... and found the executable "pia-client"

I added /opt/piavpn/bin/pia-client - u to the start up app and it starts  my app (pia) on start up.

HOWEVER, as noted by TheFU, adding an app at startup that needs working network service doesn't make sense! What happens in my case is that the pia app launches and waits for network service.

HOpe this helps somebody.

Too old to have fun Old Jimma From THe Old Country

---

### Post by #&amp;thj^% on 2020-11-11
Would'nt this be easier?
See Screenshot.

---

### Post by TheFu on 2020-11-11
> **1fallen said:**
> Would'nt this be easier?
See Screenshot.

Definitely.  I used to use PIA, but never setup automatic start with networking startup.  My need wasn't always, just about 10% of the time.

This is one example of where withholding information about the program would have really make life easier for answers.  There is a PIA.service file that can be dropped into a specific location under /etc/ with a dependency that networking is up, but not yet called "online" for VPN services like this.  Google would easily find guides for it with the 10 line .service file.

A trick might be needed if openvpn was being used - you'd want to add an authentication line .... hang on let me look it up ... to any of the .ovpn client config files
```
auth-user-pass /etc/openvpn/login.cf
```
Then in that file, are 3 lines:
```
{username}
{password}


```Be certain the last line is empty. Something like this for PIA:
```
x55583234
NdM83JTf3


```
You may want to setup AES256 on your machine and only connect to AES256 PIA servers too. By default, they use 128-bit AES.

Or use wireguard.

---

### Post by #&amp;thj^% on 2020-11-11
> **TheFu said:**
> 
Or use wireguard.

Yup!! Just keeps getting better. :) I also use PIA sparingly now, about 4 VPN providers in use here. (It pays dividends being a tester.)
[TunSafe]("https://tunsafe.com/download") has some easy and free setups. (I use my own for my own peace of mind)
EDIT: when i mention easy, I should also note that a kernel version 5.6 and up is needed to install/enable WireGuard.

---

### Post by Old Jimma on 2020-11-12
icking the "launch on start up" box on PIA adds PIA to the Ubuntu start up app.

It would be useful for discussants to provide data that can be used to compare Wireguard and OpenVPN.

ALso, it would add greatly to the discussion to know when users "need" a VPN and do not "need" a VPN. That would be illuminating.

Thank you!
Old Jimma

---

### Post by TheFu on 2020-11-12
There are lots and lots of reputable articles about the differences between Wireguard and OpenVPN.  I'm moving to wireguard for technical and ease of use reasons. Other people may have different reasons for staying or moving.

I use VPNs when I'm away and want to access my systems. I run the VPN server.

I use VPNs when I'm at home and want to appear to be somewhere else, often in a different country, but not always, or when I'd rather not have my ISP easily knowing my traffic purpose on any of the 64K ports. I use a paid VPN service for that.  The huge ISPs here have a capability called "deep packet inspection" which reduces the ability to hide the type of traffic, but the final target location, not the VPN endpoint, are unavailable to them ... well, unless I choose a crappy VPN provider with poor privacy settings or if I didn't go out of my way to ensure all DNS also travel through the VPN.  DNS leaks are extremely common. If you didn't go out of your way to prevent them, assume you are leaking every DNS lookup AND that your ISP and DNS provider are capturing that information.

---

