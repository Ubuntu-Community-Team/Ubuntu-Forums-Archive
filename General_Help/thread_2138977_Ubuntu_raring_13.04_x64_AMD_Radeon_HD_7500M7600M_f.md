---
title: "Ubuntu raring 13.04 x64 AMD Radeon HD 7500M/7600M fglrx issue"
date: 2013-04-25
forum: General Help
---

### Post by rechter77 on 2013-04-25
Hi friends,
I finished install my fresh Ubuntu 13.04 x64 and would like install fglrx (ATI driver).
But, I tried install the new AMD proprietary 13.4 and got a low graphics mode after reboot.
When I install both fglrx or fglrx-updates the system don't boot.
When I was using the precise version I instaled with success through repository ppa:andrikos/ppa in x86 version.
can someone please help me?

Thanks in advance.

Here is my lspci output:

christopher@inspiron:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
[COLOR=#ff0000]**00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)**[/COLOR]
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
[COLOR=#ff0000]**02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames [Radeon 7550M/7570M/7650M]**[/COLOR]
07:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 10)

---

### Post by yyyar on 2013-04-26
I have the same issue on HP Pavilion m6 with Radeon HD 7670M after upgrading from Ubuntu 12.10 to 13.04. 
I tried latest fgrlx 13.4 from AMD website, and from different PPA as well, but no luck. On 12.10 it worked with ppa:andrikos/ppa.
Looks like 13.4 does not supports kernel 3.8.0-19, or X.Org 1.13.3 properly?

lspci:
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT [Radeon HD 7670M]

Thanks for any help!

---

### Post by rechter77 on 2013-04-26
Thanks for the post!
Well, I think the way is wait for a next PPA release .... (asap) lol

---

### Post by yyyar on 2013-05-01
> **rechter77 said:**
> Thanks for the post!
Well, I think the way is wait for a next PPA release .... (asap) lol

There is a solution: [http://askubuntu.com/a/288355/154350](http://askubuntu.com/a/288355/154350)
Worked great for me. The only thing, I used xserver-xorg-video-intel_2.20.2-1ubuntu1_i386.deb instead of version described there. More info in this thread: [http://ubuntuforums.org/showthread.php?t=1930450&page=76&p=12621370#post12621370](http://ubuntuforums.org/showthread.php?t=1930450&page=76&p=12621370#post12621370)

Hope this helps!

---

### Post by rechter77 on 2013-05-02
Thanks a lot my friend !!!!

Worked perfect to me :P

God bless you !!!! :p

---

