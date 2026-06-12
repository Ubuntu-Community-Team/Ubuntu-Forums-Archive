---
title: "ubuntu 15.10 slow boot - analysis shows 2 min till graphical.target service starts"
date: 2016-01-23
forum: General Help
---

### Post by bmullan2 on 2016-01-23
For some time now I've been dealing with an exceptionally long boot time.

Today I decided to try to figure out what's causing it.    

From the output of **systemd-analyze** I can see that the kernel startup finishes in just 13 seconds BUT the userspace takes over 3 minutes ??
Running **systemd-analyze critical-chain** shows that just getting to the point of starting "graphical.target" takes almost 2 minutes ?  

Why is this taking so long is my question?     What could the system be doing up to that point that causes a 2 minute delay ?

Note:  I've done google searches and _there seems to be a lot of people having this same slow boot problem_ 
Many of those end up pointing to this same long time span before the system even gets to the "graphical.target" service start !
SystemD seems to be one of the few things everyone has in common!

My system is an 8 core cpu,  
32GB ram 
nvidia gpu
2 TB HD - 7200rpm spinning disk - no errors being reported on it
/boot is 8GB EXT4 partition on /dev/sda1
/ and /home are on a 2TB BTRFS partition on /dev/sda6

**$ systemd-analyze**
Startup finished in 13.313s (kernel) + **3min 5.278s (userspace)** = 3min 18.592s

**$ systemd-analyze critical-chain**
**The time after the unit is active or started is printed after the "@" character.**
The time the unit takes to start is printed after the "+" character.

[B]graphical.target @_1min 57.783s_
[/B]--multi-user.target @1min 57.783s
----lxc.service @1min 57.267s +515ms
------lxc-net.service @1min 55.702s +1.562s
--------network-online.target @1min 55.692s
----------network.target @1min 44.827s
------------wpa_supplicant.service @1min 49.084s +180ms
--------------basic.target @1min 35.033s
----------------sockets.target @1min 35.033s
------------------lxd-unix.socket @1min 35.031s +2ms
--------------------sysinit.target @1min 35.028s
----------------------systemd-timesyncd.service @16.809s +65ms
------------------------systemd-remount-fs.service @8.044s +103ms
--------------------------system.slice @4.935s
-----------------------------.slice @4.935s

---

### Post by ajgreeny on 2016-01-23
If you choose the Advanced options from grub and then choose to boot the **upstart** version for the same kernel, does the system boot much faster or do you suffer other problems?

What about using another earlier kernel if you have one?

---

### Post by bmullan2 on 2016-01-23
thanks for the reply... but I found at least 1 problem and fixed it & cut the time from 1 min 58 seconds to just 58 seconds ... still not good but 50% better

The UUID for my swap partition was bad so I did the following:

$ sudo mkswap /dev/sda5

   That remakes a swap and gave it a new UUID,

Then I edited /etc/fstab and duplicated the line for swap & commented out the original line to preserve

Finally in the new swap line I deleted the old UUID and replaced it with the NEW UUID provided by the mkswap


That cut my boot time from 2 minutes to 58 seconds which still needs to get fixed but its much faster than before.


Since I have 32GB ram I'd just never looked/checked my swap before now.   I actually got the hint to look at it from some other people who after upgrading to 15.04 (and/or 15.10) found their swap UUID bad as I did.

So now I'm left with 3 things to look at:

1)  on my machine at _every_ boot I see 
    Searching for BTRFS
    then an FSCK runs

2) $ systemd-analyze
      Startup finished in 13.487s (kernel) + **51.555s (userspace)** = 1min 5.042s

    $ systemd-analyze blame
         [B]16.450s NetworkManager-wait-online.service
         13.372s plymouth-read-write.service[/B]
         etc... rest are all in the millisecond range

So I need to figure out why FSCK is being run at every boot (again disk checks fine each time & when I check it manually) ?

But also it seems to me that 16 seconds for NetworkManager and 13 seconds for Plymouth services still seem way too long ?

Brian

---

### Post by rawcoder on 2016-01-23
*NetworkManager-wait-online.service* internally uses *nm-online* to detect whether you are online or not.  It has *timeout* parameter which you can adjust.  By default, its value is 30.  You can use a lower value.

The file is at **/lib/systemd/system/NetworkManager-wait-online.service**

---

### Post by bmullan2 on 2016-01-23
Thanks rawcoder... but I'd already done that and change the timeout for it to 15

---

### Post by bmullan2 on 2016-01-25
Well I found and fixed 1 problem ...

On my 15.10 system my SWAP UUID was NOT valid in /etc/fstab so at boot Swap was not getting mounted.
I found this after doing some google searches.   
Apparently quite a few people had the same problem and its not just with Ubuntu (arch & other OS as well).

Because the /etc/fstab SWAP UUID was incorrect SWAP **was not** getting mounted at boot and I guess systemD either keeps on trying or reaches a time-out I don't know which.

How did I check this...  I ran the Ubuntu DISKS app and saw my SWAP partition did not have a little arrow on it indicating it was "mounted".    
If you suspect you are having the same problem you can check yours that way to.
 
To fix that problem I did the following...

IMPORTANT:  in the following MY SWAP partition is /dev/sda5 ... **yours is probably different** DO NOT use /dev/sda5 but use whatever yours is !!   Again, the DISKS app can tell you what /dev/sdxx your swap is on.


[LIST=1]
[*]sudo mkswap /dev/sda5                    # That'll remake swap and give it a new UUID,
[*]Edit /etc/fstab                                   #**In the line for swap **delete the old UUID and replace it with the NEW UUID you got from step #1
[*]reboot                                              # after reboot you should now see that your SWAP is being mounted correctly
[/LIST]


That cut my boot time from 2 minutes to 58 seconds !!

Still not where I want it BUT its much faster than before.   So I've still got more investigating to do.

---

