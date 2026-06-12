---
title: "Help! - Rescue my linux box before I wipe it / networking"
date: 2021-05-08
forum: General Help
---

### Post by jamiewightwick on 2021-05-08
**Ubuntu 20.04 LTS**

Hi all,

First time poster - I desperately need help!

I was having some problems yesterday with getting a connection to my VPN by openvpn; the error logs suggested it was a look up problem, so I googled around and found etc/resolv.conf. I saw the DNS was set to 127.0.0.53, and thought that seemed weird (thought it might be leftover setting of the VPN) so I changed to 8.8.8.8. The thread I was on suggested this would be fine.

I rebooted the PC, and now it won't boot up - because it keeps tripping over the openvpn@openvpn service file I have; it can't connect, so the device never boots. 

It's hard to read the sprawl of info, but it looks to me as if a few potentially network-related services are failing to start - I can see network name resolution, Avahi mDNS/DNS-SD stack, and the Bluetooth service - before it moves onto trying openvpn and fails.

Things I remember trying (sorry, was working on this in a panic well into the night):


[LIST]
[*]Generic recovery mode; still got stuck
[*]Tried to pull up a terminal while it was booting; I can't seem to do this reliably - I tried CTRL + ALT + F1 - F7, and sometimes it seemed to work and others not.
[*]When I did get the terminal up - I would try disabling the service with 'sudo systemctl disable [email]openvpn@openvpn.servic[/email]e', and it would look like it was deleting the sym links, but upon reboot nothing had changed
[*]Tried making a live ubuntu USB, booting into the try me mode and then mounting the system block so I could edit files that way; I tried setting /etc/resolve.conf back to what it was, and again it looks like it's saved during the session, but it didn't make a difference upon reboot.
[/LIST]

PLEASE help - I've got backups of lots of important config and service files, but for various reasons the time I have to tinker with this stuff anymore is extremely limited, and the thought of having to spend hours after bedtime each night next week to wipe it and freshly reinstall everything is bringing me close to tears! :)

Thanks :)

---

### Post by dddman on 2021-05-08
There's a ton of easy to use backup.  Why must you spend sleepless nights restoring?  Mine just takes a few clicks, yours should too.

I am clueless as to how a vpn ends up as part of the boot process.  That suggest you have to be hooked to the internet for your computer to work at all.  I do not think this is so.

---

### Post by jamiewightwick on 2021-05-08
I'm not really sure how it ended up being something that stops the computer booting, but nevertheless *shrugs.* I think I'm going to have to wipe it and hope I've got most of the important scripts and settings backed up. What do you recommend for future use, incidentally?

---

### Post by HermanAB on 2021-05-08
Try something like this first:
Boot with install media, mount the root partition (just click on it with the file explorer).  Find the VPN config file with the file explorer.  Open a terminal and delete the VPN configuration file (or just rename it to vpnconfig.bad).  Then reboot again and see what happens.

BTW, the resolv.conf file is created by the network manager utility, so if you manually edit it, the change will be gone on the next reboot.  To make changes permanent requires editing a different file to preset the values you want.

---

### Post by TheFu on 2021-05-08
Disabling the VPN stops it until the next boot, doesn't it?  Perhaps it needs to be mask'd?
```
sudo systemctl mask [email]openvpn@openvpn.service
```
which will prevent it from starting until you 'unmask' it.

systemctl disable DOES NOT STOP any service.  The 
```
sudo systemctl stop
``` command is required for that.

The /etc/resolv.conf gets re-written whenever systemd-resolved notices it has changed. That could be once per boot or much more often. There is a local DNS caching server running, since most home users would like that to speed up their internet.  127.0.0.53 is that local caching service port.  Any service on 127.x.x.x/8 is something used by the "localhost" and is not accessible by any other system on the LAN. It is not considered to be a security issue.

I suspect something else, unrelated to what you are doing, is causing the boot issues.  Look at the boot logs.    **journalctl -b**  and **journalctl -xe** should help with that.  If older boots aren't being saved, you can tweak the /etc/systemd/journald.conf  file to keep them for a few boots or by a size that is limited.
```
[Journal]
Storage=persistent
SystemMaxFileSize=500M
```

Are the settings I've changed, but really 100M should be 10x larger than needed. The manpage for that file explains lots of the other options.  They are explained in the typical systemd-documentation style which will eventually be correct, but might not yet be correct on your system. On the internet, it has been called "aspirational documentation."

---

### Post by Skaperen on 2021-05-08
127.0.0.53 is just a way to track what's going on when to port number cannot be seen.  every IP address in the 127.0.0.0/8 subnet will reach any localhost listener.  this is done so that traffic that is based on reading that address shows up as addresses to that address.  you can change it to 127.0.0.54 and DNS queries will then go to 127.0.0.54 and will still work.  back when used Slackware, i manually set it up with 127.0.0.53, myself.  it comes in handy when you want to filter what traffic you see in tcpdump using just addresses (to see any DNS queries going to the wrong place).

---

### Post by jamiewightwick on 2021-05-10
Hi all,

Just wanted to say thank you to you guys for your suggestions! I thought I had switched on email notifications for replies but clearly I didn't. Those are some really helpful suggestions - definitely making some notes in big book of Linux stuff about the boot journal! - But alas/fortunately I bit the bullet in the end and went for the nuclear wipe and reinstall option.

Thankfully, my very basic home made backup script had got 90% of the important stuff squirreled away, and my Linux-fu has clearly improved over the years as it didn't take me half as long as I thought to put the world to rights (although still most of Sat night into early sun!)

I learned a lot doing it actually, and if nothing else it helped me identify the holes in the stuff I back up and make some really useful reminder notes to myself in future about the various pitfalls I encountered along the way should something like this happen again.

Thanks again for all the helpful suggestions, much appreciated :)

---

