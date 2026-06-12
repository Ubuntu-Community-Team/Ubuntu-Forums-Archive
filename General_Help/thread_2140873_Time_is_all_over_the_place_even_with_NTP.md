---
title: "Time is all over the place even with NTP"
date: 2013-04-30
forum: General Help
---

### Post by hotspear on 2013-04-30
Hi Experts,

I am having issues with times on ubuntu 12.10 and 13.04, server and desktop.

I have NTP and likewise-open running. I ran 
```
ntpdate -q nz.pool.ntp.org
```
every 10 minutes

And here is the result:
```
server 203.109.252.7, stratum 3, offset 0.009650, delay 0.02667
server 202.6.116.123, stratum 2, offset -0.002035, delay 0.02638
server 203.97.109.165, stratum 2, offset -0.004516, delay 0.04834
 1 May 13:44:08 ntpdate[28935]: adjust time server 202.6.116.123 offset -0.002035 sec
server 203.97.109.165, stratum 2, offset -0.004576, delay 0.04814
server 203.109.252.7, stratum 3, offset 0.009687, delay 0.02660
server 202.6.116.123, stratum 2, offset -0.002050, delay 0.02640
 1 May 13:44:17 ntpdate[28961]: adjust time server 202.6.116.123 offset -0.002050 sec
server 202.21.137.10, stratum 1, offset 77.004827, delay 0.03708
server 202.78.240.38, stratum 2, offset 77.005159, delay 0.03563
server 182.54.165.145, stratum 2, offset 77.007598, delay 0.05807
 1 May 14:00:07 ntpdate[31790]: step time server 202.21.137.10 offset 77.004827 sec
server 119.47.118.129, stratum 2, offset 77.002382, delay 0.02734
server 219.89.199.51, stratum 2, offset 76.997650, delay 0.04314
server 117.18.82.7, stratum 2, offset 77.009817, delay 0.03760
 1 May 14:10:08 ntpdate[982]: step time server 119.47.118.129 offset 77.002382 sec
server 203.109.252.7, stratum 3, offset 144.017701, delay 0.02666
server 202.6.116.123, stratum 2, offset 144.005733, delay 0.02638
server 202.78.240.38, stratum 2, offset 144.006584, delay 0.03568
 1 May 14:20:08 ntpdate[3055]: step time server 202.6.116.123 offset 144.005733 sec
server 202.6.116.123, stratum 2, offset 223.008696, delay 0.02635
server 202.21.137.10, stratum 1, offset 223.008885, delay 0.03716
server 203.99.129.34, stratum 2, offset 223.000291, delay 0.02768
 1 May 14:30:07 ntpdate[5016]: step time server 202.21.137.10 offset 223.008885 sec
server 60.234.251.225, stratum 2, offset 3.020140, delay 0.04958
server 117.18.82.8, stratum 2, offset 3.019038, delay 0.03758
server 203.118.148.40, stratum 2, offset 3.015346, delay 0.05095
 1 May 14:40:53 ntpdate[6176]: step time server 117.18.82.8 offset 3.019038 sec
server 202.21.137.10, stratum 1, offset 3.014950, delay 0.03749
server 203.97.109.165, stratum 2, offset 3.011206, delay 0.04845
server 202.6.116.123, stratum 2, offset 3.014780, delay 0.02637
 1 May 14:50:07 ntpdate[7702]: step time server 202.21.137.10 offset 3.014950 sec
server 203.99.129.34, stratum 2, offset 71.013228, delay 0.02754
server 60.234.251.225, stratum 2, offset 71.025155, delay 0.04961
server 119.47.118.129, stratum 2, offset 71.020614, delay 0.02736
 1 May 15:00:08 ntpdate[9492]: step time server 119.47.118.129 offset 71.020614 sec
server 203.99.128.34, stratum 2, offset 5.024953, delay 0.03732
server 203.99.129.34, stratum 2, offset 5.016144, delay 0.02759
server 202.78.240.38, stratum 2, offset 5.024495, delay 0.03552
 1 May 15:10:07 ntpdate[10957]: step time server 203.99.129.34 offset 5.016144 sec

```

I tried different time servers in /etc/ntp.conf and got the same results.

Can you please advise what could be wrong?

Thanks heaps

---

### Post by TheFu on 2013-05-01
I don't have any clue, but would guess that your motherboard clock is toast.  First thing that I would try, before throwing out the motherboard, is to swap the CMOS battery to see if that helps.

Also, maintaining time inside a virtual machine is different with and without the "guest additions", so if you are doing any VM work, it would be critical to state it.

Lastly, if stability is more important than anything else, run 12.04 LTS, not the other releases.

---

### Post by rnerwein on 2013-05-01
hi
just a question - how does your /var/lib/ntp/ntp.drift file looks like (-16.073). i am running 12.04 LTS but should be no reason.
output looks different too:
 ntpdate -q nz.pool.ntp.org
server 203.99.128.34, stratum 2, offset -0.002907, delay 0.34207
server 203.118.148.40, stratum 2, offset -0.002741, delay 0.36391
server 203.99.129.34, stratum 2, offset -0.005041, delay 0.35532
 1 May 15:44:21 ntpdate[10891]: [COLOR=#0000ff]adjust time server[/COLOR] 203.99.128.34 offset -0.002907 sec
always the same
ciao

---

### Post by SeijiSensei on 2013-05-01
You might consider running the NTP daemon and letting it manage the machine's time.  Install the **ntp** package and give that a try.

---

### Post by hotspear on 2013-05-01
Thanks for all the replies. I did install ntp package.

Hardware clock was one of the things I suspected. But 
```
hwclock -r
```
shows consistently the correct time while 
```
date
```
jumps around.

/var/lib/ntp/ntp.drift was a non-zero value. I tried changing it to 0 or back to whatever it was, didn't make any difference.

I also suspect the time was set via likewise-open through domain controller. But the time on the windows domain controller is correct.

The same thing happens on 3 different installations. 
12.04 LTS on bare metal
13.04 on VMware
13.04 on bare metal

Also 
```
ntpq -p
```
shows no entries with * in front when time is off. But there are always a few entries:
```

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 msltime.irl.cri .ATOM.           1 u   12   64   77   11.479  77991.3 58957.7
 gardyneholt1.ga 202.46.181.123   2 u   48   64  177    2.226  77989.2 63681.3
 ns1.deakin.edu. 169.254.0.1      4 u   51   64  177   39.152  77996.3 63682.8
 203.171.85.237. .PPS.            1 u   44   64  177   61.343  77990.7 63681.6

```

Thanks again

---

### Post by TheFu on 2013-05-01
Don't use MS-Windows to control time.  It can't keep time in my experience.  Active Directory/Domains are **known** to be off up to 5 minutes in many environments.  However, Windows can point to a UNIX/Linux time server and maintain accurate time.

NTP is millisecond accurate. It works and it works exceptionally well on UNIX/Linux environments, if following the best practices.

If you run VMware ESX/ESXi, **do not** use NTP to control the client NTP clocks.  Install the guest additions and let the ESX control system time that way. [http://communities.vmware.com/message/2039852](http://communities.vmware.com/message/2039852) explains.

The ntp.drift file is not something we control. It is maintained automatically by NTP as it figures out how much network delay and clock drift is usual for our system. DO NOT ATTEMPT to edit this file.

There are only a few lines in the /etc/ntp.conf file that matter. 2 should point to NTP servers on the internet - something like:
**server pool.ntp.org**
is an example.  

NTP needs for the current system time to be reasonably close to the real time - within 30 minutes, but less than 5 minutes is best. If it is off by more than that, it may not converge over time to the correct, nearly exact, time.  Stop the NTP service, set the correct time and timezone, restart NTP and it will slowly, gradually, migrate to the correct time. It does this to prevent time sensitive programs from being too screwed from quick changes.  The offsets in your output above make me think you have the wrong timezone set and/or  you are not pointing to time servers near your network location. Can you confirm?

If the machines are running near full CPU utilization, time services are not always maintained. This can allow for more drift than desired. On most systems, this slight slowdown of the clock isn't an issue for 15 minutes at a time, NTP will correct it.  However, on systems that run full out for hour after hour after hour, the system clock can easily get out of time and might need to be manually corrected.  I've never seen this myself, since running systems constantly over 90% utilized is not a good idea.

Anyway, a few more ideas for your consideration.

---

### Post by hotspear on 2013-05-01
I didn't mean to use Windows domain controller to set time on linux. I just installed likewise-open and joined the domain. I only suspect likewise-open could change the time but that's only a suspicion.

hwclock -r is very close to the correct time and it doesn't change a lot. But "date" does.

I am in New Zealand. I use
nz.pool.ntp.org
as my server, along with default servers from ubuntu. I changed a  few servers and they are all same.

Server is not busy at all. CPUs are running under 20% over 95% of the time. That's why I am so confused. As you can see in my first post, my time changes from 0 second off to 223 seconds off 1.5 hours later then back to 5 seconds off 40 minutes later.

What else could cause the problem?

---

### Post by TheFu on 2013-05-01
Interesting.  Never heard of "likewise-open" - interesting.  A google discovered this: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1036328](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1036328)
My shop doesn't use Windows, so I can't test the issue. Sorry.  The things you are reporting sound like the behavior I saw using Windows Servers for time. Until I stopped doing it, the clocks were always off.

I'd start by checking all the log files in /var/log/ for hints of an issue. Hopefully, some error or warning will jump out.

Unrelated, but have you looked at Samba4 as an option for domain membership instead of likewise?  I know zero about it.

Clearly, I haven't got a clue. I'd look for specific bugs related to the specific versions of ntp running on each of your machines too.  Those offsets and jitter values are troublesome.  [https://www.linuxquestions.org/questions/linux-server-73/ntp-offset-value-too-high-881554/](https://www.linuxquestions.org/questions/linux-server-73/ntp-offset-value-too-high-881554/) talks more about it, but I don't know if I believe the ideas presented.

Completely off topic - I've always wanted to visit NZ!  Seems like a wonderful place in the world.  Got back from Nepal last month and planning a Cape Town trip later this year.

---

### Post by hotspear on 2013-05-06
I think I've sussed out this problem. It looks like it's still caused by likewise-open. It is strange as the windows domain controller has the right time. Possibly different time sync systems have conflicts.

Anyway, to disable likewise-open to sync time with domain controller:
```

sudo lwregshell set_value '[HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory]' "SyncSystemTime" 0

```

Times are all right for the past 2 hours or so. So fingers cross, hopefully this is the fix.

---

