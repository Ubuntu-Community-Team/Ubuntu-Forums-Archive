---
title: "Freezing problem in Google browser."
date: 2023-02-06
forum: General Help
---

### Post by satimis on 2023-02-06
Hi all,

Ubuntu 22.04
[B][U]
Recently discover freezing problem in Google browser.[/U][/B]

It is very strange that Google browse freezes occasionally.  Particularly when upload a image file to my website working on it.

Other running applications are still working without problem.  I have to logout and re-login then Google browser works again.

Also when I attach a file to my Yahoo mail, the browsing function for files without response.

Please advise where I have to check to solve the problem.  Thanks in advance.

Regards

---

### Post by kc1di on 2023-02-07
I have a similar problem on vivaldi Browser which is based on Google Chrome.  I only have to go out of the browser and relaunch it to fix it.  But it is annoying at times. 
I find that the problem is often caused by hardware acceleration.  Try disabling it in Chrome see if it stop happening.

---

### Post by satimis on 2023-02-07
> **kc1di said:**
> I have a similar problem on vivaldi Browser which is based on Google Chrome.  I only have to go out of the browser and relaunch it to fix it.  But it is annoying at times. 
I find that the problem is often caused by hardware acceleration.  Try disabling it in Chrome see if it stop happening.
Hi,

Thanks for your advice.

It is very funny to me.  Google and Firefox are running on this 2TB NVMe PCIe 3.0 SSD.  The problem mentioned just happens recently about one week.

I have another 1TB NVMe PCIe 3.0 SSD on this PC.  Google and Firefox are also running on it but without such problems.

I wonder whether I need to re-install both of them ?

Regards

---

### Post by kc1di on 2023-02-07
I would try the hardware acceleration first.  If that does not work maybe reinstall.

---

### Post by satimis on 2023-02-07
> **kc1di said:**
> I would try the hardware acceleration first.  If that does not work maybe reinstall.
Hi,

Following your advice, I have un-checked "Use hardware acceleration when available"
Please refer to screenshot attached.

Problem still remains.

Let me explain further.
I have 3 Chrome windows running. Only the Chrome window trying to upload image freezes.  The other 2 Chrome windows are working without problem, including other applications.

According to my recollection I have installed Google extension before.  Would it be a problem?  Thanks

Regards

---

### Post by kc1di on 2023-02-08
Well the one way to find out if it's an extension causing the problem would be to disable the all and add them back one at a time. See what happens.

---

### Post by satimis on 2023-02-08
> **kc1di said:**
> Well the one way to find out if it's an extension causing the problem would be to disable the all and add them back one at a time. See what happens.
Hi,

It is extremely funny to me.  I can't reply you on Firefox running on Host because unable to attach the screenshot of extensions.  Clicking "browse" (file) is without response.  I have to reply you on the Firefox of Ubuntu 22.04 VM.

Please refers to screenshot attached.

Regards

---

### Post by monkeybrain20122 on 2023-02-08
> **satimis said:**
> Hi,

It is extremely funny to me.  I can't reply you on Firefox running on Host because unable to attach the screenshot of extensions.  Clicking "browse" (file) is without response.  I have to reply you on the Firefox of Ubuntu 22.04 VM.


Regards

Because firefox is a snap?

---

### Post by DuckHook on 2023-02-08
Like you and kc1di, this happens to me on Brave, which is also derived from the same foundations as Vivaldi and Chrome. And like kc1di, I can recover by killing Brave and relaunching, which will then pick up the session at the exact point at which it froze, even if it was password protected or in the middle of a download (which is sorta freaky when you think about it). At least I'm relieved to know that I'm not alone.

Nerfing HW acceleration only reduces the frequency of freezes but doesn't eliminate them. I doubt that the problem has anything to do with your SSDs. It is likely due to some obscure config setting in the browser or some combination of settings between the browser and the OS. My logs tell me nothing and it's both infrequent and innocuous enough that I can't really muster the motivation to track it down and squash it.

---

### Post by satimis on 2023-02-08
> **monkeybrain20122 said:**
> Because firefox is a snap?
Noted and thanks

Regards

---

### Post by satimis on 2023-02-08
> **DuckHook said:**
> Like you and kc1di, this happens to me on Brave, which is also derived from the same foundations as Vivaldi and Chrome. And like kc1di, I can recover by killing Brave and relaunching, which will then pick up the session at the exact point at which it froze, even if it was password protected or in the middle of a download (which is sorta freaky when you think about it). At least I'm relieved to know that I'm not alone.

Nerfing HW acceleration only reduces the frequency of freezes but doesn't eliminate them. I doubt that the problem has anything to do with your SSDs. It is likely due to some obscure config setting in the browser or some combination of settings between the browser and the OS. My logs tell me nothing and it's both infrequent and innocuous enough that I can't really muster the motivation to track it down and squash it.
Hi,

Thanks for your advice.

Because of so many problems on Firefox, Chrome and unable to set Static IP etc., I'm prepared to wide out the drive and reinstall Ubuntu 22.04.

This is a brand new 2TB NVMe PCIe 3.0 SSD purchased about 2 moths ago.  I don't thank that there will be a problem on this SSD neither having problem on this PC.  Other drives are working without problem on this PC.

PC - AMD 8-core with 32G RAM onboard
500G SATA3 SSD - Ubuntu 22.04 and KVM
1TB NVMe PCIe 3.0 SSD - Ubuntu 22.04 and VirtualBox
1TB SATA3 SSD - Windows 11

One additional question on reinstall Ubuntu 22.04;
Do I need to run fdisk to wide-out the complete content on this 2TB NVMe PCIe 3.0 SSD?  Or just reinstall Ubuntu 22.04, letting the installer to erase all old content?

Thanks

Regards

---

### Post by DuckHook on 2023-02-08
Umm&#8230; that's awfully strong medicine for what seems to be a small and manageable problem.

If your problem was unique and not shared by others, then I would say, go ahead and reinstall. But since it is shared by kd1di and me, then I doubt that a reinstall will get you any further than where you are right now.

You did not mention that you are running VBox until now. You may want to try the following first before nuking your current install:

Switch to KVM for your VM. I used to run VBox but made the switch a few years ago&#8212;first, by running both side by side&#8212;but eventually giving up on VBox and relying solely on KVM. I switched because, at the time, I found KVM to be more stable, better supported, more powerful and far less problematic than VBox. Since I haven't used VBox for so long, I am not qualified to comment on its present state. Maybe it's gotten better, but I'm not going back.

If a different hypervisor solves your problems, then this will eliminate the need for a reinstall.

If you do decide to reinstall, you don't really need to wipe your previous install. The way that SSDs work, the old HDD advice for total erasure don't apply and do more harm than good. This is due to the fact that SSDs have microcontroller chips in them that automagically spread out system data throughout the drive. They simply do not work on a sector and platter physiology, so the old erase techniques do nothing but shorten the life of your SSD.

Just let the install process erase your old content. It's not really "erased", but it won't come back to bother you either.

---

### Post by satimis on 2023-02-08
> **DuckHook said:**
>  - snip -
Switch to KVM for your VM. I used to run VBox but made the switch a few years ago—first, by running both side by side—but eventually giving up on VBox and relying solely on KVM. I switched because, at the time, I found KVM to be more stable, better supported, more powerful and far less problematic than VBox. Since I haven't used VBox for so long, I am not qualified to comment on its present state. Maybe it's gotten better, but I'm not going back.

- snip -
Thanks for your advice.

KVM and VBox are not running on the same drive.  I can't open both of them at the same time.

Brave browser is not running on all drives in this PC.

I'm interested to find out the cause of the present problem on this 2TB NVMe PCIe 3.0 drive, if possible, for learning.  It just happened about one week.

Regards

---

### Post by DuckHook on 2023-02-08
> **satimis said:**
> …KVM and VBox are not running on the same drive.  I can't open both of them at the same time.
Sorry. I should have been clearer. I didn't mean at the same time. To my knowledge, you can't run them at the same time. By "side by side" I meant that I had them both installed and could run one or the other for purposes of comparison. VBox was always slower, more crash&#8209;prone and less flexible than KVM.

I didn't know that you already have KVM. Therefore, it would be simple for you to install Chrome in KVM and see if it still gives you the same problems.
> Brave browser is not running on all drives in this PC.

I'm interested to find out the cause of the present problem on this 2TB NVMe PCIe 3.0 drive, if possible, for learning.  It just happened about one week.

Regards
Well, if you want to track down the problem for learning purposes, I would suggest looking first at your logs, especially right after a freeze. You might also consider launching Chrome from a terminal to see what error messages pop up as the app is running. I don't see what reinstalling will do to further your goal of self&#8209;education though.

Once again, I doubt that your 2TB SSD has anything to do with the problem, but if you are unsure of drive integrity, then look at its smartmon data. With NVMEs this requires new tools:```
sudo apt install nvme-cli
sudo nvme smart-log /dev/nvme0n1p1
```Make sure you substitute whatever your real device is for "nvme0n1p1"

---

### Post by satimis on 2023-02-08
> **DuckHook said:**
> Sorry. I should have been clearer. I didn't mean at the same time. To my knowledge, you can't run them at the same time. By "side by side" I meant that I had them both installed and could run one or the other for purposes of comparison. VBox was always slower, more crash&#8209;prone and less flexible than KVM.

Noted and thanks

> 
I didn't know that you already have KVM. Therefore, it would be simple for you to install Chrome in KVM and see if it still gives you the same problems.
Chrome is also running on the 500G SATA3 SSD, having KVM installed.  I'll check it later

But on this 2TB NVMe PCIe 3.0 SSD drive when Chrome freezes VBox is not up running.  Also on the 1TB NVMe PCIe 3.0 SSD drive, Chrome won't freeze when VBox is up running

> 
Well, if you want to track down the problem for learning purposes, I would suggest looking first at your logs, especially right after a freeze. You might also consider launching Chrome from a terminal to see what error messages pop up as the app is running. I don't see what reinstalling will do to further your goal of self&#8209;education though.

Yes, I'll check Chrome log file when it freezes.

> 
Once again, I doubt that your 2TB SSD has anything to do with the problem, but if you are unsure of drive integrity, then look at its smartmon data. With NVMEs this requires new tools:```
sudo apt install nvme-cli
sudo nvme smart-log /dev/nvme0n1p1
```Make sure you substitute whatever your real device is for "nvme0n1p1"
Pls explain "Make sure you substitute whatever your real device is for "nvme0n1p1"". Thanks.

By the way on Firefox Yahoo mail unable to browse computer for attaching files where I have to check?  Thanks

Regards

---

### Post by satimis on 2023-02-09
Hi DuckHook

Just checked the 500G SATA3 SSD, having KVM installed.  Chrome and Firefox are also running on the SSD.

Chrome - no freezing problem on upload files
Firefox - able browsing computer to find and to attach files.

Those problems only happen on the 2TB NVMe PCIe 3.0 SSD drive.

Why?

I suspect whether those problem are caused in setting Static IP.  I have encountered lot of problem on setting Static IP.  Please refers to following posting;

About set up Static IP on LAMP server
[https://ubuntuforums.org/showthread.php?t=2483189&page=5&p=14130069#post14130069](https://ubuntuforums.org/showthread.php?t=2483189&page=5&p=14130069#post14130069)

Regards

---

### Post by DuckHook on 2023-02-09
> **satimis said:**
> …Pls explain "Make sure you substitute whatever your real device is for "nvme0n1p1"". Thanks.
What is your NVME device actually called? If it is, say, nvme2, then the above example code won't work.
> By the way on Firefox Yahoo mail unable to browse computer for attaching files where I have to check?
It is difficult to follow your questions because you fail to provide your system topology. Where do have FF installed? If you have FF in a separate VM from the one that you want to attach files, then they don't share any directories, so it is no wonder that you can't find any files in common to share.
> **satimis said:**
> Just checked the 500G SATA3 SSD, having KVM installed.  Chrome and Firefox are also running on the SSD.
Again, don't assume that we know your system topology. You have me thoroughly lost among your different SSDs, VMs and multiboots. This is the first time you mention a 500GB drive. Up to now, it was just a 1TB NVME and a 2TB NVME. Please don't assume that we can read your mind.
> Chrome - no freezing problem on upload files
Firefox - able browsing computer to find and to attach files.

Those problems only happen on the 2TB NVMe PCIe 3.0 SSD drive.

Why?Dunno. But you have already been given a strategy for diagnosis;. review logs and launch from command line to see any error messages.
> I suspect whether those problem are caused in setting Static IP.  I have encountered lot of problem on setting Static IP.  Please refers to following posting;

About set up Static IP on LAMP server
[https://ubuntuforums.org/showthread.php?t=2483189&page=5&p=14130069#post14130069](https://ubuntuforums.org/showthread.php?t=2483189&page=5&p=14130069#post14130069)
*sigh*

First time you've mentioned static IP. While I doubt that this is the problem, nonetheless, you really need to post the complete picture of your topology, layout and anything that departs from a standard install before anyone can help you. Otherwise, we waste our time making suggestions that are not applicable or are based on the wrong assumptions.

If your static IP was misconfigured, I would think that you wouldn't be able to surf at all. I don't see how it would only effect uploads. I hope that a network guru might comment on this. Did you change to static IP just before the problems started? If so, then there may be a connection.

Can you switch to dynamic IP? Does the problem go away if you do so?

That's how we chase down issues on these forums. If you suspect something, you change that setting. This either eliminates that suspicion or confirms it.

---

### Post by satimis on 2023-02-10
> What is your NVME device actually called? If it is, say, nvme2, then the above example code won't work.
Hi DuckHook

Sorry.

$ sudo fdisk -l | grep nvme```

Disk /dev/nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
/dev/nvme0n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2 1050624 2000408575 1999357952 953.4G Linux LVM
Disk /dev/nvme1n1: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
/dev/nvme1n1p1    2048    1050623    1048576  512M EFI System
/dev/nvme1n1p2 1050624 3907028991 3905978368  1.8T Linux LVM

```
**[COLOR="#FF0000"]nvme1n1[/COLOR]**

$ cat /etc/netplan/01-network-manager-all.yaml ```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```
There is no settings on .yaml

$ ip a | grep inet```

    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
    inet 192.168.1.165/24 brd 192.168.1.255 scope global dynamic noprefixroute enp4s0
    inet6 fe80::eff6:efed:843d:dc77/64 scope link noprefixroute 

```
I suppose 192.168.1.165 is dynamic IP as it said```

inet 192.168.1.165/24 brd 192.168.1.255 scope global dynamic noprefixroute enp4s0

```

Now all problems mentioned previously in this thread are gone.
1)
Chrome won't free when uploading files
Remarks:
Same files and same website for this testing

2)
Yahoo mail on Firefox
-> browsing computer works for seleting files to attach to the email and sent

I suspect the encountered problems being caused by Netplan.  As mentioned on my #16 posting above, no such problems found if setting Static IP via interfaces, if-up and if-down route

Besides, I also have encountered problems in setting Static IP on VMs.  Now although Static IP set but the mouse pointer is jerking, difficult to control.

Regards

---

### Post by satimis on 2023-02-10
Hi DuckHook,

Further to my previous posting

Now this 2TB NVMe SSD drive is unble to boot, dropping to GRUB.  Please see my posting #51 on following thread;
[https://ubuntuforums.org/showthread.php?t=2483189&page=6&p=14130214#post14130214](https://ubuntuforums.org/showthread.php?t=2483189&page=6&p=14130214#post14130214)

Maybe I can rescue it using the Ubuntu 22.04 boot USB.  Following article suggests many rescue methods;

Classic SysAdmin: How to Rescue a Non-booting GRUB 2 on Linux
[https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux)

I don't know how long I have to dragging along?  If I fail to rescue this 2TB NVMe SSD drive, I would erase it and reinstall Ubuntu 22.04 on it.

I won't try Netplan again to set Static IP.  The old way is very reliable.

Host:
Create /etc/network/interfaces file with following content;```

    # interfaces(5) file used by ifup(8) and ifdown(8)
    auto lo
    iface lo inet loopback
    dns-nameservers 8.8.8.4  8.8.4.4
    # The primary network interface
    auto enp0s3
    iface enp0s3 inet manual
    # add bridge ports
    auto br0
    iface br0 inet static
            address         192.168.1.164
            network         192.168.1.0
            netmask         255.255.255.0
            broadcast       192.168.1.255
            gateway         192.168.1.1
            bridge_ports    enp0s3
            bridge_fd       9
            bridge_hello    2
            bridge_maxage   12
            bridge_stop     off

```

Static IP 192.168.1.164

VM
Use GUI installation```

Activities
    Settings -> Network -> Wired
    click the small icon on the right
    on Wired window
    -> IPv4
    IPv4 Method
    (check) Manual
    Addresses
    Address [192.168.1.165  ]
    Netmask [255.255.255.0  ]
    Gateway [192.168.1.1    ]
    DNS [8,8,8,8, 8.8.4.4 ]
    Routes     Automatic (select)
    -> Apply (right top corner)

```
Static IP 192.168.1.165

I have been running them for long time on both Ubuntu 20.04 and Ubuntu 22.04 without fail

No addition application is required.

Regards

---

### Post by monkeybrain20122 on 2023-02-10
> **DuckHook said:**
> Like you and kc1di, this happens to me on Brave, which is also derived from the same foundations as Vivaldi and Chrome. And like kc1di, I can recover by killing Brave and relaunching, which will then pick up the session at the exact point at which it froze, even if it was password protected or in the middle of a download (which is sorta freaky when you think about it). At least I'm relieved to know that I'm not alone.


I also use brave. No problem here, smooth as butter. Do you have a Nvidia card? (Intel here)

---

### Post by satimis on 2023-02-10
> **monkeybrain20122 said:**
> I also use brave. No problem here, smooth as butter. Do you have a Nvidia card? (Intel here)
Hi,

I don't have Brave browser running.  Graphic come from AMD CPU.

There are no problem on other drives in this PC
1)
500G SATA3 SSD - running Ubuntu 22.04 and KVM
2)
1TB NVMe PCIe 3.0 - running Ubuntu 22.04 and VirtualBox

Static IP of Host and VM/guest are set via Interfaces and GUI mentioned on my previous posting.  NetPlan is NOT installed.

3) Windows 11

This PC is an AMD 8-core PC with 32G RAM onboard and has been running for at 5 years without problem.  I have been struggling on Netplan for more than 2 weeks without end.

Regards

---

### Post by DuckHook on 2023-02-10
> **monkeybrain20122 said:**
> I also use brave. No problem here, smooth as butter. Do you have a Nvidia card? (Intel here)
AMD
```
duckhook@Zeus:~$ sudo lshw -c display
  *-display                 
       description: VGA compatible controller
       product: Navi 22 [Radeon RX 6700/6700 XT / 6800M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: /dev/fb0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=amdgpu latency=0 resolution=3840,2160
       resources: irq:171 memory:90000000-9fffffff memory:a0000000-a01fffff ioport:3000(size=256) memory:a0300000-a03fffff memory:a0400000-a041ffff
```
I try to stick to AMD because of the problems that many forum members have reported with NVidia. AMD seems to cooperate better with the Linux community.

I should note that I run all of my browsers within LXD containers. That may have something to do with the issue. satimis also seems to be having trouble with Brave within a VM, so it is possible that our sandboxing is the problem. I can't see why though. My FF, Epiphany and Tor Browser run just fine and they are sandboxed in the same way. I don't know about kc1di.

@kc1di

Do you run Vivaldi within a sandbox of some kind? Is it a snap version?

---

### Post by DuckHook on 2023-02-10
> **satimis said:**
> I suspect the encountered problems being caused by Netplan.  As mentioned on my #16 posting above, no such problems found if setting Static IP via interfaces, if-up and if-down route
I've found that the best way to set a static IP is not to do so on my clients, but on my DHCP server. For most SOHO users, this would be their router.

That way, you leave your client installs in their default state (dynamic IPs), but the router assigns them the same IP every time anyway, so it is essentially static.
> Besides, I also have encountered problems in setting Static IP on VMs.
If you want to assign a static IP to a NAT&#8209;ted VM (though I don't know why one would do that), then I believe that all VMs have provisions for setting static IPs for any client. Again, one does not have to change the client's defaults or monkey around with netplan.

In fact, the only reason that I configure netplan (or Network Manager) uniquely is when I want to add VPN. Even then, I run the VPN in a container, modify my network settings within the guest container and leave my host alone.

The major theme I'm trying to convey is: leave your base install (your host) in as close to default state as possible.
> Now although Static IP set but the mouse pointer is jerking, difficult to control.
Again, more unexpected info about your topology is coming to light. Are you using WIFI to network? Because if you are, then all bets are off. WIFI is known to interfere with wireless mouse. Bluetooth too. It may also explain VM freezing problem. WIFI cannot spoof a MAC address, so you may need to make special provisions if you want to bridge network a VM for example. If not WIFI, then the problem is elsewhere.
> **satimis said:**
> …Now this 2TB NVMe SSD drive is unble to boot, dropping to GRUB.…I don't know how long I have to dragging along?  If I fail to rescue this 2TB NVMe SSD drive, I would erase it and reinstall Ubuntu 22.04 on it…
…I won't try Netplan again to set Static IP. 
Given that you now cannot boot, and we don't know what changes you've made to your install on NVME1, perhaps it is best in your case to just reinstall. This time, do not mess with the defaults after you install. Since your 2TB NVME is nvme1, then before installing, first check the health of the drive with:```
sudo nvme smart-log nvme1
```

After installing, leave your network alone (in its default state) and assign static IP through your router.

---

### Post by xinuzi on 2023-02-10
(desktop) Firefox = these days, very very good (it seems me so).

---

### Post by satimis on 2023-02-10
> 
**[COLOR="#FF0000"]Originally Posted by DuckHook[/COLOR]**
If you want to assign a static IP to a NAT&#8209;ted VM (though I don't know why one would do that), then I believe that all VMs have provisions for setting static IPs for any client. Again, one does not have to change the client's defaults or monkey around with netplan.

I would stick on the 2 methods mentioned on #19 above, to set Staiic IP which I have been used for years without problem.

1) /etc/network/interfaces
OR
2) GUI via Activities -> Settings etc.

This time I try to learn something new to me running Netplan, coming to the present situation.

I would wide out the 2TB NVMe SSD drive and reinstall Ubuntu 22.04

> 
**[COLOR="#FF0000"]Originally Posted by DuckHook[/COLOR]**
Again, more unexpected info about your topology is coming to light. Are you using WIFI to network? Because if you are, then all bets are off. WIFI is known to interfere with wireless mouse. Bluetooth too. It may also explain VM freezing problem. WIFI cannot spoof a MAC address, so you may need to make special provisions if you want to bridge network a VM for example. If not WIFI, then the problem is elsewhere.

No WIFI, cable connection only

> 
**[COLOR="#FF0000"]Originally Posted by DuckHook[/COLOR]**
Given that you now cannot boot, and we don't know what changes you've made to your install on NVME1, perhaps it is best in your case to just reinstall. This time, do not mess with the defaults after you install. Since your 2TB NVME is nvme1, then before installing, first check the health of the drive with:

I haven't made any change on the 2TB NVMe SSD after sorting the freezing problem.  Then I turned off the PC for dinner.

Before reinstall I would check the health of the SSD as advised running;
```

sudo nvme smart-log nvme1

```
Also I would disconnect all other drives in this PC before reinstallation

Thanks

Regards.

---

### Post by satimis on 2023-02-10
Hi DuckHook,

Ran your suggested command to check 2TB NVMe PCIe 3.0 SSD

$ sudo nvme smart-log nvme1```

nvme1: No such file or directory
Usage: nvme smart-log <device> [OPTIONS]

Retrieve SMART log for the given device (or optionally a namespace) in either
decoded format (default) or binary.

Options:
  [  --namespace-id=<NUM>, -n <NUM> ]   --- (optional) desired namespace
  [  --output-format=<FMT>, -o <FMT> ]  --- Output format: normal|json|binary
  [  --raw-binary, -b ]                 --- output in binary format
  [  --human-readable, -H ]             --- show info in readable format

```

$ sudo fdisk -l | grep nvme```

Disk /dev/nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
/dev/nvme0n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2 1050624 2000408575 1999357952 953.4G Linux LVM
Disk /dev/nvme1n1: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
/dev/nvme1n1p1    2048    1050623    1048576  512M EFI System
/dev/nvme1n1p2 1050624 3907028991 3905978368  1.8T Linux LVM

```

$ sudo nvme smart-log /dev/nvme1n1 > nvme1n1.txt

$ cat nvme1n1.txt
```

Smart Log for NVME device:nvme1n1 namespace-id:ffffffff
critical_warning			: 0
temperature				: 32 C (305 Kelvin)
available_spare				: 100%
available_spare_threshold		: 10%
percentage_used				: 0%
endurance group critical warning summary: 0
data_units_read				: 12,448,420
data_units_written			: 16,584,005
host_read_commands			: 1,106,256,291
host_write_commands			: 61,982,961
controller_busy_time			: 744
power_cycles				: 322
power_on_hours				: 75
unsafe_shutdowns			: 14
media_errors				: 0
num_err_log_entries			: 0
Warning Temperature Time		: 0
Critical Composite Temperature Time	: 0
Temperature Sensor 1           : 32 C (305 Kelvin)
Temperature Sensor 2           : 38 C (311 Kelvin)
Thermal Management T1 Trans Count	: 0
Thermal Management T2 Trans Count	: 0
Thermal Management T1 Total Time	: 0
Thermal Management T2 Total Time	: 0

```

**[COLOR="#FF0000"]critical_warning			: 0[/COLOR]**

Is there any problem on this SSD drive ?

Regards

---

### Post by DuckHook on 2023-02-10
The drive looks healthy. Note:```
media_errors				: 0
num_err_log_entries			: 0
Warning Temperature Time		: 0
Critical Composite Temperature Time	: 0
Temperature Sensor 1           : 32 C (305 Kelvin)
Temperature Sensor 2           : 38 C (311 Kelvin)
```
No media errors. Temps are all good.

But look at this:```
unsafe_shutdowns			: 14
```
Any unsafe shutdown is risking the integrity of your OS. 14 of them almost certainly will. I would not be surprised if certain registers and configs have become corrupted because they were left in a state of suspended animation when the plug was pulled. If your system becomes unresponsive, always [try things like SysRq]("https://en.wikipedia.org/wiki/Magic_SysRq_key") before cutting power. We always try to shut down cleanly.

Do you remember why you had to shut down by brute force so many times? As said, such shutdowns play havoc with your files. Since everything on Linux is a file, it is quite possible that a series of dirty shutdowns is the cause of your problems.

---

### Post by satimis on 2023-02-11
> **DuckHook said:**
> The drive looks healthy. Note:```
media_errors				: 0
num_err_log_entries			: 0
Warning Temperature Time		: 0
Critical Composite Temperature Time	: 0
Temperature Sensor 1           : 32 C (305 Kelvin)
Temperature Sensor 2           : 38 C (311 Kelvin)
```
No media errors. Temps are all good.

But look at this:```
unsafe_shutdowns			: 14
```
Any unsafe shutdown is risking the integrity of your OS. 14 of them almost certainly will. I would not be surprised if certain registers and configs have become corrupted because they were left in a state of suspended animation when the plug was pulled. If your system becomes unresponsive, always [try things like SysRq]("https://en.wikipedia.org/wiki/Magic_SysRq_key") before cutting power. We always try to shut down cleanly.

Do you remember why you had to shut down by brute force so many times? As said, such shutdowns play havoc with your files. Since everything on Linux is a file, it is quite possible that a series of dirty shutdowns is the cause of your problems.
Sorry I couldn't recall exactly.

Occassionaly I turned off the PC while VM was still up.  Would it amount to "unsafe_shutdown" ?

Now I have reinstalled Ubuntu 22.04 on the 2TB NVMe PCIe 3.0 SSD drive and it is up running without problem.  Also I have set Static IP via Settings IPv4 route```

    Settings -> Network -> Wired
    click the small icon on the right
    on Wired window
    -> IPv4
    IPv4 Method
    (check) Manual
    Addresses
    Address [192.168.1.164  ]
    Netmask [255.255.255.0  ]
    Gateway [192.168.1.1    ]
    DNS [8,8,8,8, 8.8.4.4 ]
    Routes     Automatic (select)
    -> Apply (right top corner)

```

$ ifconfig```

enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.164  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::6c8f:e95c:ff62:aa83  prefixlen 64  scopeid 0x20<link>
        ether 04:d9:f5:7d:0e:40  txqueuelen 1000  (Ethernet)
        RX packets 51622  bytes 41562700 (41.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 37098  bytes 7877118 (7.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5094  bytes 593357 (593.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5094  bytes 593357 (593.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Chrome won't freeze. Yahoo mail on Firefox can browse computer to attach file and send mail.

The only remaining problem is the screen blinks occasionally while clicking the mouse pointer.

Where should I check ?

The remaining work is to install VirtualBox and VMs.  I have all VM images, about 10, saved on a 4TB WD drive which is solely for data storage without OS installed.

I wonder whether I should use the VMs images and create new VMs.  Those VMs images have Netplan installed for setting Static IP.  Not much work has been down on the VMs.  Actually I only worked on 3 VMs and the rests were for testing Netplan.  I only stick on those 3 working VMs

Your advice would be appreciated.  Thanks

Regards

---

### Post by satimis on 2023-02-11
Hi DuckHook,

Performed following test:

1)
After having installed VirtualBox on; virtualbox-7.0_7.0.6-155176_Ubuntu_jammy_amd64.deb
and
Create an Ubuntu 22.04 VM, then with Static IP set running GUI on Activities -> Settings

All without problem

2)
Then add a VM having Static IP set with Netplan previously

Start this VM

3)
I could find Settings on Activities.  It is because gnome-control-center missing

4)
Delete the VM including its image.  Re-install gnome-control-center.  Then Activities -> Settings is displayed.

VM with Static IP set up on Netplan also affects the Host

Regards

---

