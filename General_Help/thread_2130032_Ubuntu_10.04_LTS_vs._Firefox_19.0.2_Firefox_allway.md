---
title: "Ubuntu 10.04 LTS vs. Firefox 19.0.2: Firefox allways says &quot;Server Not Found&quot;"
date: 2013-03-28
forum: General Help
---

### Post by Bidyut Chakraborty on 2013-03-28
I am using Ubuntu 10.04 LTS. I am not able to run Firefox in it. Though my network connection is being made and I am able to download and upgrade some softwares through Ubuntu, but why Firefox not recognizing the connection? Can anybody there to help me please!

---

### Post by sanderj on 2013-03-28
Does Chrome / Chromium work?

---

### Post by Bidyut Chakraborty on 2013-04-06
@sanderj
Thank you for responding. But alas I was somehow confused how to get to this thread, being bit novice. So, I am bit late to respond.
Answering your query: I am not able to browse and thus not be able to download anything! So, I could not try any other browser at all.
Some say to disable IPV6, some other say to modify config file of Firefox. The later one I tried, but found no effect.
Please help me.
Thank you
BC

---

### Post by sanderj on 2013-04-06
what is the output of:

```
mtr -nrc2 8.8.8.8
```

Post it here

---

### Post by rnerwein on 2013-04-06
> **Bidyut Chakraborty said:**
> I am using Ubuntu 10.04 LTS. I am not able to run Firefox in it. Though my network connection is being made and I am able to download and upgrade some softwares through Ubuntu, but why Firefox not recognizing the connection? Can anybody there to help me please!
hi
have you tried: nslookup [www.google.com]("http://www.google.com")
if this don't work then try in your browser the ip (it's google): 173.194.35.176
and try: ping 173.194.35.176
if even this don't work -> you have a major problem with your network.
ciao

---

### Post by dcstar on 2013-04-07
> **Bidyut Chakraborty said:**
> I am using Ubuntu 10.04 LTS. I am not able to run Firefox in it. Though my network connection is being made and I am able to download and upgrade some softwares through Ubuntu, but why Firefox not recognizing the connection? Can anybody there to help me please!

**Edit-Preferences-Advanced-Network** and make sure the Proxies settings match what your network actually uses.

---

### Post by Bidyut Chakraborty on 2013-04-08
@sanderj: I am on move at present - when I am reading your advice. I'll certainly let you know about it (i.e. output of mtr -nrc2 8.8.8.8 ) after a day. Thank you for your response again.
@rnerwein(ciao):No I have not tried nslookup google.com. But I had once tried with google's ip address - ofcourse without any effect. I may let you know about the result of nslookup after a day. Thank you for your response.
@dcstar(David):I had set No Proxy - as per my network - and alas nothing improved. Thank you for your response.

BTW - I am using WindowsXP on the same machine. Does that cause such problem anyway?

BC

---

### Post by tgalati4 on 2013-04-08
Sometimes dual-booting will cause the network card to get messed up.  Try shutting down windows, unplug the machine for 5 minutes, then boot into linux and see if it restores your network connectivity.

---

### Post by Bidyut Chakraborty on 2013-04-08
@All: I tried [FONT=arial]mtr -ncr2 8.8.8.8[/FONT] but got blank reply. Then I tried the google ip address 173.194.35.176 and voila! Google did come. I searched for Ubuntu Forums and the Urls did appear. But clicking on them resulted in same stale reply "Page not found".
With Google logged in I again tried for mtr.... and then I found a host lot of data appeared as below:

HOST: bidyut-laptop               Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 10.102.0.65                   0.0%     2  382.6 303.0 223.5 382.6 112.5
  2. 10.102.2.21                   0.0%     2  323.8 273.5 223.3 323.8  71.1
  3. 10.133.32.244                 0.0%     2  261.0 288.1 261.0 315.1  38.3
  4. 125.22.78.54                  0.0%     2  194.2 294.7 194.2 395.2 142.2
  5. 182.79.252.182                0.0%     2  187.3 295.2 187.3 403.0 152.5
  6. 72.14.216.229                 0.0%     2  120.6 307.7 120.6 494.8 264.6
  7. 66.249.94.170                 0.0%     2  113.9 338.3 113.9 562.7 317.4
  8. 209.85.241.21                 0.0%     2  103.1 351.5 103.1 599.9 351.2
  9. 8.8.8.8                       0.0%     2   96.3 564.0  96.3 1031. 661.4

So, now I submit myself to you experts. Please do help me.
Thank you all for your valuable responses.
BC

---

### Post by Bidyut Chakraborty on 2013-04-08
@tgaliati4: Actually though my set up is for dual booting but I never switch between Windows and Linux in one go. My these trials were done by booting to Linux only. Secondly, the network connection was always made and I was able to update Ubuntu couple of times. So the problem, that I understand, is between Ubuntu and Firefox setups - which I am not able to understand. Basically I am just a beginner on Linux.
Thank you for your response.
BC

---

### Post by sanderj on 2013-04-08
> **Bidyut Chakraborty said:**
> @All: I tried [FONT=arial]mtr -ncr2 8.8.8.8[/FONT] but got blank reply. Then I tried the google ip address 173.194.35.176 and voila! Google did come. I searched for Ubuntu Forums and the Urls did appear. But clicking on them resulted in same stale reply "Page not found".
With Google logged in I again tried for mtr.... and then I found a host lot of data appeared as below:

HOST: bidyut-laptop               Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 10.102.0.65                   0.0%     2  382.6 303.0 223.5 382.6 112.5
  2. 10.102.2.21                   0.0%     2  323.8 273.5 223.3 323.8  71.1
  3. 10.133.32.244                 0.0%     2  261.0 288.1 261.0 315.1  38.3
  4. 125.22.78.54                  0.0%     2  194.2 294.7 194.2 395.2 142.2
  5. 182.79.252.182                0.0%     2  187.3 295.2 187.3 403.0 152.5
  6. 72.14.216.229                 0.0%     2  120.6 307.7 120.6 494.8 264.6
  7. 66.249.94.170                 0.0%     2  113.9 338.3 113.9 562.7 317.4
  8. 209.85.241.21                 0.0%     2  103.1 351.5 103.1 599.9 351.2
  9. 8.8.8.8                       0.0%     2   96.3 564.0  96.3 1031. 661.4

So, now I submit myself to you experts. Please do help me.
Thank you all for your valuable responses.
BC

Three consecutive 10-addresses, with an India airtel.com public IP address? On what kind of network are you?

Your mtr sometimes works, and sometimes doesn't? If so: I don't understand why that can happen.

---

### Post by Bidyut Chakraborty on 2013-04-09
@sanderj: Airtel India is my service provider for internet connection. I am using Airtel data card (dongle) for internet connection. What does it show by three consecutive addresses of Airtel in list? Can you please explain me? Well frankly I do not understand the significance of mtr output as I am not well versed with Linux and more so with such technical aspects.
Secondly, mtr was working only when I could go to Google by giving IP address of Google. But otherwise mtr was not giving any data - only the heading line was printed.
                           HOST: bidyut-laptop               Loss%   Snt   Last   Avg  Best  Wrst StDev
 Since I am able to get through IP address but not by name does it indicate some dns problem? Any solution there?
Thank you for your regular responses.
BC

---

### Post by rnerwein on 2013-04-09
> **Bidyut Chakraborty said:**
> @tgaliati4: Actually though my set up is for dual booting but I never switch between Windows and Linux in one go. My these trials were done by booting to Linux only. Secondly, the network connection was always made and I was able to update Ubuntu couple of times. So the problem, that I understand, is between Ubuntu and Firefox setups - which I am not able to understand. Basically I am just a beginner on Linux.
Thank you for your response.
BC
hi
it is - you have a problem with your resolver (DNS). please post the output of your:
/etc/resolv.conf
/etc/nsswitch.conf

and what is the answer of:
nslookup [www.google.com]("http://www.google.com")   (this will show you the address of your name-server at least because your network is working)
ciao

p.s. oh even try:
mtr [www.google.de](www.google.de)          ( not the ip-address !)
and post that output too.

---

### Post by sanderj on 2013-04-10
> **Bidyut Chakraborty said:**
> @sanderj: Airtel India is my service provider for internet connection. I am using Airtel data card (dongle) for internet connection. What does it show by three consecutive addresses of Airtel in list? Can you please explain me? Well frankly I do not understand the significance of mtr output as I am not well versed with Linux and more so with such technical aspects.
Secondly, mtr was working only when I could go to Google by giving IP address of Google. But otherwise mtr was not giving any data - only the heading line was printed.
                           HOST: bidyut-laptop               Loss%   Snt   Last   Avg  Best  Wrst StDev
 Since I am able to get through IP address but not by name does it indicate some dns problem? Any solution there?
Thank you for your regular responses.
BC

The output of "mtr -nrc2 8.8.8.8" should **always** be a list of hops. If there are no hops, you have low level network problem.

So you use a 2G/3G/4G dongle? That could be the cause of your problem: no hops can be caused by the dongle not being connected. Maybe the connection goes to sleep, or you are out of coverage due to a bad 2G/3G signal? If that happens, run "dmesg" and see at the end what it says.

---

### Post by sanderj on 2013-04-10
> **Bidyut Chakraborty said:**
> @All: I tried [FONT=arial]mtr -ncr2 8.8.8.8[/FONT] but got blank reply. 

Wait ... you tried "mtr -ncr2 8.8.8.8"? That's wrong and will give no output. It should be "mtr -nrc2 8.8.8.8" (note the order of the options)

So: **always** run "mtr -nrc2 8.8.8.8". Does that always give hops?

---

### Post by dcstar on 2013-04-10
> **Bidyut Chakraborty said:**
> @sanderj: Airtel India is my service provider for internet connection. I am using Airtel data card (dongle) for internet connection.
..........

Sometimes the Wireless Dongle connection does not set up the DNS correctly. You need to go into the Network Manager and look at the "Connection Information" and post what the Primary DNS is.

---

### Post by sanderj on 2013-04-10
> **dcstar said:**
> Sometimes the Wireless Dongle connection does not set up the DNS correctly. You need to go into the Network Manager and look at the "Connection Information" and post what the Primary DNS is.

Could be, but I would say first things first. So if "mtr -nrc2 8.8.8.8" (which does not involve DNS) does not yield hops, first solve that. And only if that always works, move on the higher level (ie DNS).

---

### Post by Bidyut Chakraborty on 2013-04-10
@rnerwein

/etc/resolv.conf
===================
nameserver 122.160.237.201
nameserver 202.56.230.7
nameserver 122.160.237.201
nameserver 202.56.230.7
nameserver 122.160.237.201
nameserver 202.56.230.7
nameserver 208.67.222.222 > changed by me
nameserver 208.67.220.220 > changed by me

/etc/nsswitch.conf
===================
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

Output of nslookup [www.google.com]("http://www.google.com")
===========================
;;connections timed out; no servers could be reached

Output of mtr [www.google.de]("http://www.google.de")
======================
Name or Service not known: No such file or directory

@sanderj
Output of dmesg
===============
<first few lines>
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-46-generic (buildd@aatxe) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #105-Ubuntu SMP Fri Mar 1 00:08:49 UTC 2013 (Ubuntu 2.6.32-46.105-generic 2.6.32.60+drm33.26)
:
:
:<last few lines>
[   24.808497] hw_cdc_check_status_work: carrier off
[   32.184639] ISO 9660 Extensions: Microsoft Joliet Level 1
[   32.223090] ISOFS: changing to secondary root
[   57.014490] PPP BSD Compression module registered
[   57.022831] PPP Deflate Compression module registered

typo: used mtr -nrc2 8.8.8.8 only - no it not always gives hops. Only when I use IP address (say connecting to google this way) the hops are given - as I posted earlier.

@dcstar: Somehow I could not find Network Manager - not in the menu that appears on the desktop screen!!

Thank you

BC

---

### Post by sanderj on 2013-04-10
> **Bidyut Chakraborty said:**
> 
typo: used mtr -nrc2 8.8.8.8 only - no it not always gives hops. Only when I use IP address (say connecting to google this way) the hops are given - as I posted earlier.


I don't understand your quoute "Only when I use IP address" as "mtr -nrc2 8.8.8.8" only contains an IP address, and will only show IP addresses. 

:confused:

---

### Post by Bidyut Chakraborty on 2013-04-10
@sanderj: Sorry for the confusion. Let me be more specific: I have always used the command "mtr -nrc2 8.8.8.8". Now when Firefox is not been able to connect at that instant this command does not show any hops. But in Firefox when I put IP address (instead of URL) and Firefox connects to the site - at this instant this command gives those hops that I posted earlier.
Hope I am now clear Sir!
BC

---

### Post by rnerwein on 2013-04-10
> **Bidyut Chakraborty said:**
> @sanderj: Sorry for the confusion. Let me be more specific: I have always used the command "mtr -nrc2 8.8.8.8". Now when Firefox is not been able to connect at that instant this command does not show any hops. But in Firefox when I put IP address (instead of URL) and Firefox connects to the site - at this instant this command gives those hops that I posted earlier.
Hope I am now clear Sir!
BC
hi
ok - you have a problem with your namesever (DHCP)
1. check if your router is configured for using DHCP.  (start firefox and give him the IP of your router. or you can run firefox from the command-line:
---> firefox 192.168.2.1  (this IP ist the IP of my router).
2. your local configuraration is configured for not using DHCP. check it with networkmanager or with the app you are using. but here i must give up -
    i am a command line junkie. my configuration in /etc/network/interfaces looks like:
    allow-hotplug wlan0
    auto wlan0
    iface wlan0 inet [COLOR=#ff0000]dhcp[/COLOR]
    .......
    .......
3. comment out your modifications in /etc/resolv.conf
4. run: ps -ef | grep dhc (is the dhclient running ?)
    have a look at: /etc/dhcp/dhclient.conf
5. restart your services (or reboot)
good luck
ciao

---

### Post by sanderj on 2013-04-11
There is only one hypothesis I can think of:

"The 2G/3G/4G is dropped (for example after a time-out). The connection is only set-up again if there is traffic over HTTP port 80 (and not by DNS traffic, so initial DNS lookups don't work)"

That's it. That would explain all the things you describe (inlcuding your DNS not working). I do not guarantee it is the reason, but it could be the reason.

Solution: find a setting that disables the connection-dropping
Workaround: create a crontab setting that each minute does "curl 173.194.78.105" to keep the connection active and thus open. Worth a try.

---

