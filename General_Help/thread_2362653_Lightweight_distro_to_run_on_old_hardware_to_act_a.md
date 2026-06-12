---
title: "Lightweight distro to run on old hardware to act as DDNS update client and RDP server"
date: 2017-05-31
forum: General Help
---

### Post by fozziebear on 2017-05-31
Apologies if I have posted this in the wrong part of the forum.
I need to set up a DDNS update client and be able to remote desktop into our local Village Hall charity to maintain three Windows 10 PCs. Although we have just upgraded to a 50Mb FTTP connection the service does not have a fixed IP and the router (unlike our previous Vigor 2820n ADSL router) unfortunately does not have the option to configure a service for No-IP DNS. There are no always on PCs/Devices to run the service.

I would therefore like to build a low power always on linux based PC that will run the No-IP DUC client and also an RDP server so that I can remote in to the hall and wake up the three Windows PCs using WOL in order to apply updates.

I have a number of small form factor PCs with Intel Pentium 4 processors or Intel Mobile processors that I would like to re-utilise as a headless server. I need to be able to RDP to the desktop of this server and then be able to RDP to each of the three PCs using a graphical interface. I am not skilled enough to use command line or SSH.

Ideally the Linux image should run from a USB/SD card or live image on a CD. Boot time is not crucial as it will be always on but should reboot automatically after a power failure
Can anyone recommend a small linux distro which has:-
1) A built in (or can be installed) RDP server
2) Will run the No-IP Ubuntu based DNS Updater client
3) Has a WOL client with Gui to wake up the three Windows PCs
4) Has an RDP Client which will work with Windows remote desktop or VNC or similar

Many thanks
Fozzie

---

### Post by ian-weisser on 2017-05-31
Even less hardware (like a Pi or similar) will reduce power consumption and can easily handle the DDNS heartbeat and WOL master that you envision.

An RDP server for such trivial tasks is overkill, and provides unnecessary attack surface.
Learn to use SSH, and use keys properly to secure it.
Learning how to safely set up and secure SSH takes about two hours.
Learning how to use SSH to install and maintain your No-IP takes about 15 minutes. Take notes.
Learning how to use SSH to install and maintain your WOL master take about 30 minutes. Take notes.
After you spend those three hours, you will wonder why you thought it was hard. It's not.

If you want to *really* become technically-minded, install Open-WRT or DD-WRT on your router, and run the services from there.
Personally, I recommend against it. I prefer to keep the router separate, so a crashed service doesn't take down the entire network too.

---

### Post by TheFu on 2017-05-31
RDP isn't secure for internet use. Neither is VNC  For that you need to use a full VPN or ssh tunnel with both of those.

ddclient is the ddns client you seek. It is in the repos. Haven't used it myself in years, but it worked well last I remember with both dyn and no-ip.

You don't need a GUI to WoL clients. Seems like a bunch of overhead for nothing.  ssh is much easier once you understand it.  Getting ssh working on a new system is about 45 seconds for me at this point. That includes never having to type a password and blocking brute force attacks.

So ... there are 2 options.

a) setup openvpn and use rdp/vnc as you planned.  OpenVPN is a very capable tool, but because it is so very capable, it is fairly complicated to setup. The web GUI for it had a nasty security bug announced last week, but if you don't use the GUI, it is fine.

b) setup an NX protocol remote desktop (which uses ssh-tunnels automatically) - something like **x2go**, then use RDP to get to the Windows machines on the LAN.  ssh is pretty trivial to setup, secure and prevent brute force attacks. This is a well understood path.  It also helps that NX is 2-3x more efficient than either VNC or RDP. It is faster.  If your client machine (the machine you use far away from the charity) is Unix-based, then ssh and x2go are a no-brainer.  If Windows, x2go has ssh built in.  All normal ssh authentication methods are supported. Only 1 port need be opened.

I use "b" all the time.  Actually, I'm using "b" right now to access my main desktop in a private cloud.

So ... there isn't a specific Linux distro just for these things.  You can install mini-Ubuntu, then add only the programs you want.  What happens after a power failure is a BIOS setting, IME.  If you want to boot from a flash drive or SD card, that is also your decision. Both will be slow.

Initially, I was going to suggest you use a raspberry Pi for this. It will certainly use less power and be less obtrusive than other options, but it is ARM, so some packages don't exist for it.

If you are going to do remote support, learning ssh really is the first step. Avoiding that is a bad idea.  Plus, if you just need to wake up a Windows machine, it is very convenient to run a remote command from the machine you are on already that uses ssh into the LAN, then sends a WoL to 1 or all the systems.  You wouldn't need to do anything more - 10 seconds of your time, tops.

Option C ... just thought about this.  Setup a pfSense router.  This provides a nice GUI to make an openvpn and has an admin gui that you can use to send WoL to any connected devices.  It also supports no-ip and many other ddns providers.  pfSense isn't consumer friendly, but it is fairly friendly for all the capabilities is provides.  It is a tiny distro and purpose built to be a gateway device for medium-sized businesses and Universities. Lots of people run pfSense at home - I do.  It is based off freeBSD with is probably the most secure network OS available today.   Maintaining pfsense is really easy. There is a config backup menu. That contains every setting for the system - everything.  New releases and updates are a 2 button process. Plus, if you use pfsense, you don't need a Linux box. That simplifies the network security, IMHO.

So, those are 3 options to consider. Each with pros/cons.

---

### Post by fozziebear on 2017-06-03
Firstly many thanks for your reply however I think you misunderstand the scenario and the suggestions to use SSH will not enable me to do what I require.
> **ian-weisser said:**
> Even less hardware (like a Pi or similar) will reduce power consumption and can easily handle the DDNS heartbeat and WOL master that you envision.

An RDP server for such trivial tasks is overkill, and provides unnecessary attack surface.As per my initial post there are NO always on devices on-site therefore nothing for the DDNS update service or WOL to run on unless I have a small machine. The biggest stumbling block is a lack of a fixed external IP address. If we had that then it opens other options as there are services that provide WOL over the internet e.g. LogMeIn etc

>  Learn to use SSH, and use keys properly to secure it.
Learning how to safely set up and secure SSH takes about two hours.
Learning how to use SSH to install and maintain your No-IP takes about 15 minutes. Take notes.
Learning how to use SSH to install and maintain your WOL master take about 30 minutes. Take notes.
After you spend those three hours, you will wonder why you thought it was hard. It's not. I don't have time to learn another command line language and unless I am completely missing the point SSH is CLI not a Gui. I need to "View" the "Gateway" machine's desktop and then be able to run RDP sessions from there to again "View" the desktops of the three computers I need to maintain. These are switched off after use so I cannot access the directly unless I use WOL on the network to wake them up first

> If you want to *really* become technically-minded, install Open-WRT or DD-WRT on your router, and run the services from there.
Personally, I recommend against it. I prefer to keep the router separate, so a crashed service doesn't take down the entire network too. These are a FTTP router and owned by the company. I am not allowed to install other software on their equipment and even if I were i very much doubt DD-WRT or Open-WRT is available for this hardware.
Thanks Again though for responding
Fozzie

---

### Post by dragonfly41 on 2017-06-03
> [COLOR=#000000]The biggest stumbling block is a lack of a fixed external IP address.[/COLOR][COLOR=#000000]
I suggest that you explore installing [ngrok]("https://ngrok.com/") on your intermediary server to expose to the internet.

It is quite easy to deploy. Then build on that to manage your devices.

I'm not sure if then installing [webmin]("http://www.webmin.com/") on your intermediary would then open up other admin services to manage your devices.
But it is worth exploring.  webmin is in Ubuntu repo.  webmin when installed is accessed through https protocol on port 10000 on host server.  You can also add Custom Commands to be run through webmin GUI.

By running webmin the intermediary server can be headless (without desktop).[/COLOR]

---

### Post by fozziebear on 2017-06-03
> **TheFu said:**
> RDP isn't secure for internet use. Neither is VNC  For that you need to use a full VPN or ssh tunnel with both of those. Agreed but I am not concerned about security. these machines are Internet Cafe workstations that have nothing on them and are locked down with software that restores the image on reboot. There is no traffic being sent to the site that is confidential or of any use to anyone 

> You don't need a GUI to WoL clients. Seems like a bunch of overhead for nothing.  ssh is much easier once you understand it.  Getting ssh working on a new system is about 45 seconds for me at this point. That includes never having to type a password and blocking brute force attacks. Agreed but as explained in my previous reply I need to "View" the desktop of the "gateway" machine running DDNS and WOL so that I can then RDP to the desktops of the three windows Internet cafe machines. I need to disable the lock down software and then re-enable after installing windows updates and I need to "See" these installing on the remote machines. Command Line instructions are not suitable if at all possible for this task.

> So ... there are 2 options.

a) setup openvpn and use rdp/vnc as you planned.  OpenVPN is a very capable tool, but because it is so very capable, it is fairly complicated to setup. The web GUI for it had a nasty security bug announced last week, but if you don't use the GUI, it is fine.

b) setup an NX protocol remote desktop (which uses ssh-tunnels automatically) - something like **x2go**, then use RDP to get to the Windows machines on the LAN.  ssh is pretty trivial to setup, secure and prevent brute force attacks. This is a well understood path.  It also helps that NX is 2-3x more efficient than either VNC or RDP. It is faster.  If your client machine (the machine you use far away from the charity) is Unix-based, then ssh and x2go are a no-brainer.  If Windows, x2go has ssh built in.  All normal ssh authentication methods are supported. Only 1 port need be opened.

I use "b" all the time.  Actually, I'm using "b" right now to access my main desktop in a private cloud. Thank you for this. I have found a similar suggestion on a ServerFault forum and one suggestion was to use NoMachine [https://www.nomachine.com/](https://www.nomachine.com/) which utilises SSH tunnelling and has a GUI allowing Remote Desktop sessions.

 >  What happens after a power failure is a BIOS setting, IME.  If you want to boot from a flash drive or SD card, that is also your decision. Both will be slow. Yes I was aware that the state after power failure was a bios setting as is WOL I just included it for completeness as some services on linux do not start on boot unless specifically configured to do so.

>  Initially, I was going to suggest you use a raspberry Pi for this. It will certainly use less power and be less obtrusive than other options, but it is ARM, so some packages don't exist for it. Yes I looked at this as I could have used Teamviewer remote support client but as I understand it wont work on a Pi without lots of hacking.

> If you are going to do remote support, learning ssh really is the first step. Avoiding that is a bad idea.  Plus, if you just need to wake up a Windows machine, it is very convenient to run a remote command from the machine you are on already that uses ssh into the LAN, then sends a WoL to 1 or all the systems.  You wouldn't need to do anything more - 10 seconds of your time, tops. As I replied earlier I need to "View" the desktop of the remote Windows machines to administer them. This includes at times "Shadowing" someone when trying to resolve a problem. The ideal solution would be a client like Teamviewer Remote support on each PC so I didnt have to worry about a gateway pc and DDNS but as the machines are powered down then I need to use WOL to access them first. TeamViewer has supposedly got WOL functionality but I have never got it to work. In fact in a previous scenario when supporting desktops where I could access an always on file server as the gatway often I had to send magic packets numerous times to wake up a client and often this wasn't successful.

> Option C ... just thought about this.  Setup a pfSense router.  This provides a nice GUI to make an openvpn and has an admin gui that you can use to send WoL to any connected devices.  It also supports no-ip and many other ddns providers.  pfSense isn't consumer friendly, but it is fairly friendly for all the capabilities is provides.  It is a tiny distro and purpose built to be a gateway device for medium-sized businesses and Universities. Lots of people run pfSense at home - I do.  It is based off freeBSD with is probably the most secure network OS available today.   Maintaining pfSense is really easy. There is a config backup menu. That contains every setting for the system - everything.  New releases and updates are a 2 button process. Plus, if you use pfsense, you don't need a Linux box. That simplifies the network security, IMHO. I had wondered about something like pfSense. Presumably I would have to put this behind the existing fibre router and disable NAT on that router. PF pfSense would then become the firewall and handle NAT and the other services you suggest. How would I access it over the internet though without using SSH Presumably I cant then install NoMachine as suggested as an alternative so back to whatever version of RDP/VNC pfSense includes/support. I think I need to read up more on pfSense

Thank you again for your detailed and considered response
Fozzie

---

### Post by dragonfly41 on 2017-06-03
Adding to post #5.
Quick search found one thread discussing [how to create webmin custom command to invoke WOL]("https://sourceforge.net/p/webadmin/discussion/600155/thread/c4f3df4f/").

---

### Post by TheFu on 2017-06-03
If you use webmin, please, please, please, only allow access via localhost. That would mean setting up either an ssh-tunnel or a full vpn.  webmin is just another bright attack point for bad guys and constantly being attacked otherwise.

You seem to have too many old-methods in your toolkit for us to help much.  Management of Windows via point-n-click is so 1990s.  I would use a devops tool for that, if I dealt with Windows.

If you learn ssh, you'd be amazed at everything it can do.  It can easily create a secure tunnel that can be a pivot for remote desktops, but you need to take the time.  

I really don't see the dynamic IPs as any issue at all.  I ran systems for a decade behind non-static IPs. It was never an issue, except trying to run SMTP. For everything else in a small business, it was a non-issue.

Your lack of concern about security is a huge concern for me.  Every system needs to be secured so it isn't used to attack others.

Use x2go.  NoMachine is less satisfying for a number of reasons.  I wouldn't touch teamviewer either. The reasons are well-known.

IMHO.  It's your issue now.

---

### Post by ian-weisser on 2017-06-03
> **fozziebear said:**
> I don't have time to learn another command line language and unless I am completely missing the point

I suspect you did perhaps miss the point:
Linux uses the building-block method.
Windows uses single-big-black-box application method.
There's a big culture difference there. You ask Linux folks for ideas, you are going to get responses with building-blocks that you can tailor to meet your need.

You must 'learn another command line language' if you wish to use a Linux-based OS anyway. You can learn it up front methodically, or you can tear your hair out learning it in haste after something crashes. It's your choice.

Since you obviously have a lot of Windows skills, SSH and similar tools won't take you three hours to learn. Much, much less. 


> **fozziebear said:**
> As per my initial post there are NO always on devices on-site therefore nothing for the DDNS update service or WOL to run on unless I have a small machine.

Yes, we got that. 
You suggested a small linux server to run some kind of RDP-like service with WOL and DDNS capability.
I suggested an even smaller, cheaper, and more robust machine to run only the WOL and DDNS only. Secure desktop-sharing over the network does not require the server at all (with some obvious exceptions).

You can insert the server, and a big application like webmin if you wish. It's your job, not mine. If it's safe and makes your job easier, do it.
I find that using Linux CLI tools makes troubleshooting easier and faster. And I use direct SSH tunneling for my desktop shadows (no server needed). But my job and situation are perhaps a bit different than yours.

---

