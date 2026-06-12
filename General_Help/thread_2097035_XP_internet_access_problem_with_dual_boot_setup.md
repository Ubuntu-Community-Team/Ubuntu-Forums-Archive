---
title: "XP internet access problem with dual boot setup"
date: 2012-12-21
forum: General Help
---

### Post by duffsparkysmate on 2012-12-21
Hi All from a Ubuntu noob,

I recently resurrected a Dell Dimension 5000 desktop so that I could dual boot Windows XP and Ubuntu. The system has two 2 seperate SATA hard drives, 1 x300Gb for XP Pro(SP3) and 1 x 80 Gb for Ubuntu 12.04 LTS.

I installed the XP first on hda (300Gb) with the 80Gb drive disconnected. Then fully updated that installation and added a few goodies. This installation worked fine along with Internet access through IE and Firefox. The installation was used for  week or so before the next stage.

I then swapped the XP installed disk to hdb and connected the 80Gb disk to hda and installed Ubuntu12.04 LTS. This installation worked fine along with Internet access through Firefox.

The dual boot setup appears to work OK and I can boot into either OS at startup through the Ubuntu Grub screen. Internet access through Firefox on the Ubuntu OS works OK but I have no Internet access when running the XP installation through either IE or Firefox, although I can successfully ping my ADSL router using 192.169.1.254 (BTHomeHub 2b) from a command prompt.

I've searched through the forum but so far I have not come up with a solution, least ways not one that I recognise/understand.

Any help will be much appreciated, though please bear in mind I'm a Linux/Ubuntu green horn and my networking skills are not that great either.

Many thanks.

---

### Post by oldfred on 2012-12-21
Welcome to the forums.

Did you switch XP back to sda? I am surprised it would work if you did not but Ubuntu/grub does some mapping of drives to make Windows think it still is sda even when sdb. But none of that should be an Internet issue.

If you totally power down and reboot directly into XP does it then work?

I vaguely remember several years ago a similar issue and we all said they boot separately so their is no issue. It turned out Windows did not correctly re-initialize the modem as it always assumed you were rebooting from Windows. And the Linux driver totally reset it on shutdown. So it was a software issue. No idea what solution was.

---

### Post by carl4926 on 2012-12-22
I can't quite understand why all the drive juggling. Regardless though, it shouldn't have any effect on the network.

---

### Post by Impavidus on 2012-12-22
> **oldfred said:**
> 
I vaguely remember several years ago a similar issue and we all said they boot separately so their is no issue. It turned out Windows did not correctly re-initialize the modem as it always assumed you were rebooting from Windows. And the Linux driver totally reset it on shutdown. So it was a software issue. No idea what solution was.
There definitely was a problem like that, I used to have it myself. Unfortunately, I can't recall the solution.

---

### Post by duffsparky on 2012-12-22
> **oldfred said:**
> Welcome to the forums.

Did you switch XP back to sda? I am surprised it would work if you did not but Ubuntu/grub does some mapping of drives to make Windows think it still is sda even when sdb. But none of that should be an Internet issue.

If you totally power down and reboot directly into XP does it then work?

Ubuntu 12.04 is Drive 0/SATA 0
WinXP is Drive 1/SATA 1

[LIST]
[*]Powered down overnight -> Rebooted PC with above arrangenment ->Ubuntu Grub boot option screen appears -> selected WinXP -> PC boots into XP OK -> Internet problem still exists.
[*]Disconnected Drive 0/SATA 0 then booted -> BIOS displays error, Drive 0 not found press F1 etc etc -> PC booted into WinXP with no problem -> Internet problem still exists.[/LIST]

> **carl4926 said:**
> I can't quite understand why all the drive juggling. Regardless though, it shouldn't have any effect on the network.I just followed instructions found on this forum. If you can point me to an alternative method I'd willing to give it a go. Reformatting and starting again is not a problem.

---

### Post by oldfred on 2012-12-22
The only reason to keep Windows XP as sda, is that it hard codes the drive & partition into the boot.ini file. And BIOS typically writes info on which is boot drive that systems have to read.  So installing Windows into sdb and booting Ubuntu from sda often does not work. It usually depends on BIOS on perhaps some other issues. Of course none of that is related to Internet. I just did not think Windows would directly boot after power down.

Boot from total powerdown into Windows should allow it to totally reset.

Post this but edit out HWaddr

sudo ifconfig

and from Windows post ipconfig

---

### Post by duffsparky on 2012-12-22
Reply removed because it was not complete when accidentally posted.

---

### Post by oldfred on 2012-12-22
I was hoping you could copy & paste to a file & reboot or copy to another machine to see what settings are and compare to Ubuntu's settings.

---

### Post by duffsparky on 2012-12-22
I was just editing my reply, which is now removed, *(because I accidentally posted it before it was complete)* and went to post it but my session had timed out so the reply was lost. How do I stop this from happening again. I don't have access to the forum CP

---

### Post by duffsparky on 2012-12-22
I was already checking the win ipconfig/all results and comparing them with a good WinXP machine. Below are the results for both machines. 

I also carried out ping commnd from both machines to the other. I tried to turn off the dual boot machine's XP firewall but immediately it was switch off the anti-virus (Sophos) flagged up a treat with the following message - **'Suspicious behaviour' HIPS/RegMod-008 has been detected and moved to quarantine. Access denied,** and the firewall was back on again. The AV quarantine lists the threat in C:\WINDOWS\system32\rundll.exe

---------------Results from WinXP/Ubuntu dual boot machine-----------

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\newadmin>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : dimension-5000
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : home

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : home
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Controller
        Physical Address. . . . . . . . . : {edited}
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.65
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.254
        DHCP Server . . . . . . . . . . . : 192.168.1.254
        DNS Servers . . . . . . . . . . . : 192.168.1.254
        Lease Obtained. . . . . . . . . . : 22 December 2012 21:05:39
        Lease Expires . . . . . . . . . . : 23 December 2012 21:05:39

C:\Documents and Settings\newadmin>ping 192.168.1.77

Pinging 192.168.1.65 with 32 bytes of data:

Reply from 192.168.1.77: bytes=32 time<1ms TTL=128
Reply from 192.168.1.77: bytes=32 time<1ms TTL=128
Reply from 192.168.1.77: bytes=32 time<1ms TTL=128
Reply from 192.168.1.77: bytes=32 time<1ms TTL=128

Ping statistics for 192.168.1.77:
    Packets: Sent = 4, Received = 4, Lost = 4 (0% loss),
Approximate round trip times in milliseconds
    Minimum =0ms. Maximum - 0ms, Average = 0ms

C:\Documents and Settings\newadmin>


---------------Results from good WinXP only machine--------------

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\newadmin>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : T645
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : home

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : home
        Description . . . . . . . . . . . : Intel(R) PRO/100 S Desktop Adapter
        Physical Address. . . . . . . . . : {edited}
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.77
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.254
        DHCP Server . . . . . . . . . . . : 192.168.1.254
        DNS Servers . . . . . . . . . . . : 192.168.1.254
        Lease Obtained. . . . . . . . . . : 22 December 2012 14:00:25
        Lease Expires . . . . . . . . . . : 23 December 2012 14:00:25

C:\Documents and Settings\newadmin>ping 192.168.1.65

Pinging 192.168.1.65 with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 192.168.1.65:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

C:\Documents and Settings\newadmin>

-----------------------Results of sudo ifconfig for dual boot machine---------

glenn@Ubuntu-Dimension-5000:~$ sudo ifconfig
[sudo] password for glenn: 
eth1      Link encap:Ethernet  HWaddr (edited)  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe10:c076/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35915 (35.9 KB)  TX bytes:31440 (31.4 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23846 (23.8 KB)  TX bytes:23846 (23.8 KB)

glenn@Ubuntu-Dimension-5000:~$

---

### Post by oldfred on 2012-12-22
I cannot see anything. 

So maybe it is something with firewall or virus check software. I used to have a lot of trouble with that when I still ran XP. Part of why I prefer Ubuntu. :)

---

### Post by duffsparky on 2012-12-23
I've tried an early XP restore but that made no difference so I'm gonna go for a complete re-install of both WinXP and Ubuntu 12.04 LTS.

As my first dual boot attempt appears to have gone wrong, can you point me to a method that may be better/easier.

Many thanks.

---

### Post by oldfred on 2012-12-23
Your install process seems fine. I prefer to have Windows on one drive, sda and Ubuntu on another drive as sdb and I like each drive to be totally independent. Or you can boot each from BIOS or one time boot key without other drive. 
Some suggest disconnecting drive. But if installing Ubuntu to sdb, without disconnecting drive you do have to use manual install or Something Else to get the choice on where to install the grub2 boot loader. But best 

When you originally installed Windows did everything work as it was supposed to?

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by duffsparky on 2012-12-25
> **oldfred said:**
> Your install process seems fine. I prefer to have Windows on one drive, sda and Ubuntu on another drive as sdb and I like each drive to be totally independent. Or you can boot each from BIOS or one time boot key without other drive. 
Some suggest disconnecting drive. But if installing Ubuntu to sdb, without disconnecting drive you do have to use manual install or Something Else to get the choice on where to install the grub2 boot loader. But best 

Because the PC is going to be my Ubuntu machine I wanted the default boot to be Ubuntu, which is why I chose the dual install method detailed in my OP.
The BIOS doesn't support one-timeboot-key, though I'm gonna see if I can find a workaround for it

> **oldfred said:**
> [QUOTE=oldfred;12418678]When you originally installed Windows did everything work as it was supposed to?
As far as I'm aware everything worked OK in the WinXP and had been doing so for a few of weeks.

> **oldfred said:**
> [QUOTE=oldfred;12418678]Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)
I'd seen the article at your first link but chose a method found on this site because it gave me Ubuntu boot priority - Maybe that is the problem.

I'll the try the first method again on the rebuild and if the problem still exists I'll try again but the alternative way. I'm gonna to create a WinXP with SP3 install CD first to cut down on reinstall time.

I hadn't seen the articles at the other 2 links so I'll give them a read.

Thanks and Season's Greetings.

---

### Post by afoin on 2012-12-25
Ubuntu is using eth1, so did you install an additional network card on your computer?

---

### Post by duffsparky on 2012-12-27
> **afoin said:**
> Ubuntu is using eth1, so did you install an additional network card on your computer?

Apologies for the delay in replying.

There is only one network card in the machine at the moment but there could have been another ethernet NIC and or a wireless as well, I'm not sure when I took the others out.

I'm in the process of re-installing XP with SP3 on the original XP hard drive(sd1) at the moment, however, it is connected in the sd0 position because the install wanted to install boot info in a new partition on sd0 but there is no room for another partition.

---

