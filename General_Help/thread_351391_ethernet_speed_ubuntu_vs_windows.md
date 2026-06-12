---
title: "ethernet speed ubuntu vs windows"
date: 2007-02-01
forum: General Help
---

### Post by m.musashi on 2007-02-01
Does anyone know if there is any reason why a network speed test in ubuntu would be slower than in windows? I was having some speed issues and called tech support. I use ubuntu nearly all the time but since they don't support linux I had to boot windows. When I did, the speeds I was getting were much higher. In ubuntu I get around 2mbps using [www.speakeasy.net](www.speakeasy.net) and in windows I get 4-6mbps. That's a pretty significant difference and there was literally only about 2 minutes between tests. When I rebooted ubuntu I was back to 2mbps. I thought it might have something to do with the firewall so I disabled it but that didn't change anything.

Any other thoughts? I can't think of any reason why ubuntu would be slower - I would have expected just the opposite.

Thanks.

Oh, I use comcast cable internet if that is important and edgy.

EDIT: I think I have figured this out. See my last post.

---

### Post by scrooge_74 on 2007-02-01
Have you check the thread about IPv6?  

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

---

### Post by m.musashi on 2007-02-01
> **scrooge_74 said:**
> Have you check the thread about IPv6?  

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

Thanks for the help. I have ipv6 disabled in firefox (about:config) and I followed someone's advice and "blacklisted" ipv6 but I had not tried that particular fix. Assuming I followed it correctly it did not change anything. Here is the first part of the modprobe.d/aliases file. Did I enter the changes correctly?
```
# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
#alias net-pf-10 ipv6
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth
```

---

### Post by marx2k on 2007-02-01
It's easier than that. You don't need to touch that file at all..

'sudo gedit /etc/modprobe.d/blacklist'

type 'blacklist ipv6'

You're set

---

### Post by m.musashi on 2007-02-01
> **marx2k said:**
> It's easier than that. You don't need to touch that file at all..

'sudo gedit /etc/modprobe.d/blacklist'

type 'blacklist ipv6'

You're set

That is what I had done originally but since I am getting such disparate speeds between windows and ubuntu I thought maybe that wasn't working. Since I had it blacklisted and still had speed problems, maybe it isn't a ipv6 issue. Are there any other possible explanations?

---

### Post by Patrick K on 2007-02-02
In windows there is a setting for the TCP window. I don't know what it is but optimizing on my win box helped the speed. How it might be set on Linux, I have no idea. It may already be optimized.

---

### Post by muguwmp67 on 2007-02-02
I don't think it should matter, but are you using the same version of java on both machines? (Assuming the speed test is a java applet, most are)

Are you behind a router?  Are you using DHCP to configure the machine in both windows and ubuntu?

---

### Post by Arup on 2007-02-02
If you have ADSL, have you set your MTU correct, also your TCP receive settings, check out [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed) and also this page for setting up mtu at [http://ubuntuforums.org/showthread.php?t=82093](http://ubuntuforums.org/showthread.php?t=82093)

---

### Post by laidback on 2007-02-02
When installing Ubuntu on a friends PC we had this problem, the ISP is Virgin.

I found that the system defaulted to DHCP in Ubuntu, I cancelled that and set the connection to DNS with appropriate DNS server addresses. WOW, it steams along now, faster than in XP, and download speeds are in the region of 420kb/s on a 2Mb line. Nearly 10 times the speed I get on a 512Kb/s line. Updates are magic!!

His installation is several months old now and continues to perform at the same speed. We're both delighted.

---

### Post by m.musashi on 2007-02-02
Thanks for all the helpful suggestions.

> **muguwmp67 said:**
> I don't think it should matter, but are you using the same version of java on both machines? (Assuming the speed test is a java applet, most are)

Are you behind a router?  Are you using DHCP to configure the machine in both windows and ubuntu?

It could be a java issue. I hadn't thought of that. I think java in Ubuntu is not the same version in windows (probably because they don't use the same version numbers but it could be older).

I do use DHCP in both windows and Ubuntu. My guess is it has to be something related to the os because the modem and router settings do not change. Could be Java.

> **Arup said:**
> If you have ADSL, have you set your MTU correct, also your TCP receive settings, check out [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed) and also this page for setting up mtu at [http://ubuntuforums.org/showthread.php?t=82093](http://ubuntuforums.org/showthread.php?t=82093)

I'm using cable but I just switched from DSL. I did not have these issues with DSL but then I don't remember the last time I ran a speed test. Since I just switched to cable I wanted to check and when I saw the low numbers thought it was a comcast problem as it usually is.

An interesting side note: I switched out my new linksys modem for an older motorola and my speed jumped way up - back to the 4-6mpbs I expected. Thinking the linksys cable modem was defective I exchanged it for a new one and set it up. And what do you know, I'm back to 1-2mbps. I called linksys and explained the problem and they told me the modem was defective and I should exchange it for a third one. However, when I boot windows the same linksys modem runs at 4-6mbps. So there seems to be an issue with Ubuntu and the linksys modem that does not exist with the motorola in Ubuntu or with the linksys in windows. Very odd and frustrating. I'd just write it off and not worry if it's just a speed test quirk but everything "seems" to move slower so I can't help wondering if there is something going on. Ipv6 was a good bet but that didn't change anything.

Thanks again for the help.

---

### Post by scrooge_74 on 2007-02-02
Probably is a driver issue with the Linksys

---

### Post by m.musashi on 2007-02-02
> **scrooge_74 said:**
> Probably is a driver issue with the Linksys

I didn't know modems had drivers (unless you use usb connection - I'm ethernet). Any idea how I fix it? Since the router sits between the modem and computer I'm not even sure the computer "knows" the modem is there.

---

### Post by m.musashi on 2007-02-03
Okay, since java could be an issue with speed tests, I decided to try and find an alternative method to compare my download speeds between Ubuntu and windows. I don't know if this is less prone to problems but I decided to try and download a large file and track the download speeds.

In Ubuntu, the download stableized at about 70-90 kbps
In windows, it stabelized at about 140-170 kbps

(Yes, those both seemed low considering my broadband connection but download is also influenced by the upload speed of the sending server. Since I used the exact same file on the same server for both and there was only a few minutes between each test I'm thinking it's reliable)

So, I'm thinking this is pretty good evidence that some setting or characteristic in Ubuntu is affecting my internet connection speed.

Ipv6 is disabled.

I'm on comcast cable.

I use a linksys router attached to a linksys cable modem.

Modem and router settings are exactly the same for both Ubuntu and windows.

I would really like to figure this out. I use Ubuntu nearly 100% of the time but the difference in download speed is perceptible and frustrating.

Thanks again for the help.

---

### Post by m.musashi on 2007-02-03
Still trying to figure this out. I decided to see what would happen if I used my laptop to download the same file. Running Ubuntu it is downloading at 250-350kbps. Windows actually picked up speed to and is running at the same speed. I reboot into Ubuntu on the desktop and try again with the same file and it's still only at less than 100kbps while the laptop is still running at 250-350 in almost the same edgy install. Ipv6 is NOT disabled on the laptop so I decided to re-enable it on the desktop. It might actually be running a hair faster but it's really not noticable - still at around 100 kbps.

I must have goofed something up on the desktop. I can't imagine why it would run slower that the laptop or windows.

Anyway, I hope these clues are helpful to someone. So far I can't figure it out.

Thanks.

EDIT: one more clue. I also have a dapper install on the desktop. I booted dapper and download speeds were consistent with windows and edgy on the laptop - ie they were good.

So, the only problem is on edgy on the desktop. Clearly something is goofed up. I'm contemplating a reinstall but even thought it's relatively easy it's still a pain.

EDIT2: speakeasy speed test on laptop - 6634 kbps. Two seconds later on desktop 2412 kbps. Both running edgy. What gives?

---

### Post by m.musashi on 2007-02-04
Well, I solved this the only way I know how - reinstall. I now have download speeds on par with windows and dapper on this computer as well as the laptop. I have no idea why it was acting slow but there must have been something messed up because a reinstall fixed it. I'll keep track of packages I install incase one of them is the culprit.

---

### Post by m.musashi on 2007-02-04
Okay. Sorry for so many posts on this but I think I've solved the problem and thought I'd post on the off chance this helps someone.

I don't know why, but it seems that firestarter is causing the problem. After reinstalling, I was getting 6mbps+ so I figured that whatever was causing the problem was gone. I proceeded to reinstall various packages and one was webfs. In order to use that I had to install firestarter to allow traffic on a port. I had to reboot to get everything working and when I did my internet speed dropped again to the familiar 1-2mbps. Thinking it might be either webfs or firestarter I uninstalled one and then the other. No change. I rebooted and then I was back to 6mbps. I then reinstalled firestarter and without even rebooting I was back to 1-2mbps. I then uninstall, reboot and everything is good again.

So, it sounds like a firestarter problem.

But wait, there's more. In order to test this theory I installed firestarter on the laptop. Guess what? No Change! Damn. I was so hopping that would be it. My only guess is that somehow firestarter is conflicting with something on my desktop but I can imagine what. I have /home on a separate partition so maybe some messed up config file is hiding there and activating when I install firestarter. I'll keep digging.

At least I know what's causing it.

Thanks again.

---

### Post by erik_boi on 2007-02-04
Just posting here to verify that I am having these same problems. It was driving me nuts trying to figure out what was causing this. Thanks for finding the source. 

I don't have to remove firestarter but just changing the "internet connected device" to my unused onboard networking card, reboot, and not open the program brings my download speeds from 100-140KB/s to ~1.2MB/s.

---

### Post by dvdadog on 2008-03-22
Just wanted to say thanks for the info.  I was having the same problem getting half the download speed in Gutsy as I was in XP.  Once I changed the ethernet card in firestarter and rebooted, speed is back to flying.  Thanks again.

---

