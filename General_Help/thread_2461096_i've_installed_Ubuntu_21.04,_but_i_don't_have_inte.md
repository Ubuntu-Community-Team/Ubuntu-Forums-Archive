---
title: "i've installed Ubuntu 21.04, but i don't have internet."
date: 2021-04-24
forum: General Help
---

### Post by ronjjjg8885 on 2021-04-24
so i've tried to go to recovery mode and chose 'start network' but it got stuch after a moment and i've needed to reboot.

in earlier versions of ubuntu i had a similar problem from time to time.

perhaps i need to update firmware again?

i'm using windows 10 to write to you this messege..

thanks

---

### Post by robert48 on 2021-04-24
Are you connecting by wi-fi or ethernet cable?

---

### Post by TheFu on 2021-04-24
> **ronjjjg8885 said:**
>  i'm using windows 10 to write to you this messege..

Nothing is EVER that bad!  Say it isn't so!?  Keep a boot flash drive/sdcard at the ready with a Try Ubuntu environment - always.

---

### Post by dragonfly41 on 2021-04-24
> [COLOR=#000000]i'm using windows 10 to write to you this messege..[/COLOR]

I am approaching this bridging of Windows 10/Ubuntu worlds from a different direction.
I am experimenting with WSLg (the latest release of Windows 10 WSL) which now runs Ubuntu (full scope) inside Windows 10.  I have Ubuntu 20.04 installed in Windows 10 but I am at the point where I cannot update Ubuntu because IPv6 protocol is required.

[https://www.theregister.com/2021/04/23/wslg_first_look/](https://www.theregister.com/2021/04/23/wslg_first_look/)

It is tricky.

---

### Post by ronjjjg8885 on 2021-04-24
it a wired connection

---

### Post by dragonfly41 on 2021-04-24
> [COLOR=#000000]my desktop computer has Ubuntu 20.10 64bit alongside windows 10 as dual boot

I am just pointing out that there is another option now.
I also have Windows 10 and Ubuntu 20.04 in dual boot. In different drives.
But you cannot use them *concurrently*. It is one or the other.
With WSLg it seems we can use both OS concurrently in native Windows.[/COLOR]

---

### Post by robert48 on 2021-04-25
> **ronjjjg8885 said:**
> it a wired connection

Does your wired ethernet connection work with windows?

---

### Post by TheFu on 2021-04-25
Network Troubleshooting 101: [https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
Do those steps, in order and post the results.

---

### Post by ronjjjg8885 on 2021-05-10
> **TheFu said:**
> Network Troubleshooting 101: [https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
Do those steps, in order and post the results.

hi
i could not log in a few times.
so i didn't responded.
now it started to work again by itself.
when i occurs again i will follow your suggestions
tnx

---

### Post by TheFu on 2021-05-10
When it is broken, that's when looking at hardware issues is helpful. Always check the system logs when troubleshooting.

---

### Post by ronjjjg8885 on 2021-05-12
[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685")
i don't know how to check the system logs.

after having many bugs with Ubuntu 21.04 i've decided to switch back to Ubuntu 20.04.2.0 LTS.

to make things short.. i've the same internet problem again. so i followed the beginning of ```
https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking
``` but i didn't knew how to work with the commands after ```
ip addr
```

so i just did ```
ip addr
``` and the output attached. it is problably a problem on the computer.

[ATTACH=CONFIG]288444[/ATTACH]

is this helps you to help me solve this problem?
tnx

---

### Post by TheFu on 2021-05-12
Google found this: [https://ubuntu.com/tutorials/viewing-and-monitoring-log-files](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files)
Search term was: "ubuntu desktop log files"

Please don't post images for any terminal output. Copy/paste the information.  Nobody can highlight the text and easily point out issues to you when images are used.  The problem appears that your computer isn't getting an IPv4 address from the DHCP server (usually your router) on the LAN.

You don't know how to ping your router? Do you know the router's IP address?
```
ping whatever-that-ip-address-is
```
If a computer cannot ping the router, then that computer isn't actually on any network.  And the system log files will have some lines about that. I'm 99% certain.  Only you will be able to look at the log files and read them. Look for warnings and errors first. Then look around those - a little above and a little below - for stuff that seems related.

Don't be afraid to use google to learn stuff.  You found my *Linux 101* stuff - did you find the Linux 101 Log files article too? [https://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](https://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)
Information isn't exactly hidden on the internet, but we have to search for it.

---

### Post by ronjjjg8885 on 2021-05-12
ok
this is what i did:
i was on my windows (ubuntu's internet didin't work as you know).
i found out the ip of the router by using the ipconfig command.
then i did a ping command. and it worked. there was a ping.

then i've decided to try what you have suggested on ubuntu's again. and yet once again the internet worked again without me needing to do a thing.

now i'm on ubuntu as i said. i will try to find out how to handle log files...

edit:
which logs should i look at first? network/hardware/system? (i'm using the Log viewer (gui))

now i'm also checking pings on to the router on ubuntu...

BTW. trying to find the right information as a simple linux user is too dizzying and overwhelming for me. i will try again later and hopefully i will have more concentration for this.

---

### Post by linerman on 2021-05-14
What ethernet card have you got?

```
lspci | grep -i ethernet 
```

---

### Post by ronjjjg8885 on 2021-05-15
```
lspci | grep -i ethernet
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)


```

---

### Post by TheFu on 2021-05-15
One of my systems has that same NIC w/ the same revision.  It started failing by dropping packets. I disabled it in the BIOS and installed a cheapo skge Marvell NIC ($10 in 2006) I had laying around instead. 

The Marvell GigE is slow (maybe 300 Mbps peak), but it doesn't drop packets. It moves a bunch of data daily. I have a quad-port intel PRO/1000 NIC (have for over a year). Just need to remember to install it when the next maintenance window arrives.  I've had that quad-port card for a long time. Don't remember why it was pulled from another system - hope it works and was just being removed rather than giving it away with an old Core2 Duo box.

```
$ inxi -Nxxxz
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8168 v: 8.045.08-NAPI port: e000 bus-ID: 02:00.0 chip-ID: 10ec:8168
           IF: eth0 state: **down** mac: xx:xx:xx:xx:xx:xx
           Card-2: Marvell 88E8001 Gigabit Ethernet Controller
           driver: skge v: 1.14 port: d000 bus-ID: 04:01.0 chip-ID: 11ab:4320
           IF: eth1 state: up speed: 1000 Mbps duplex: full mac: xx:xx:xx:xx:xx:xx
```
NICs on motherboards can and do fail. Sometimes they get flaky before that failure happens. I'd bet that's what you are seeing, assuming you've swapped the cable and tried different switch ports already.

---

### Post by oldfred on 2021-05-15
You can try these commands, if you can boot to see issues.

Errors/Warnings, I get a variety of errors warnings, but none prevent system from working well:
sudo journalctl -b -p err   # q to exit log
sudo egrep -i 'warn|error' /var/log/*g

If posting terminal output, please use code tags.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by ronjjjg8885 on 2021-05-15
so if i will install a new network adapter there is a good chance it won't happen again ?
[https://pastebin.com/h4rsJXG6](https://pastebin.com/h4rsJXG6)
[https://pastebin.com/dp5etDLt](https://pastebin.com/dp5etDLt)

---

### Post by oldfred on 2021-05-15
We have seen nVidia issues cause even more errors.

dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia

What video card?
#To see video:
lspci -vnn | grep VGA -A 12
sudo lshw -c display 

One line of errors was related to fwupdate which is on line UEFI update.
My motherboard does not have and probably never will have update from fwupdate, so I just uninstall it. And it does not have bluetooth either.

If UEFI firmware update not supported (yet)
sudo apt-get purge fwupd
No bluetooth, so uninstall
sudo apt-get autoremove blueman bluez-utils bluez bluetooth

---

### Post by linerman on 2021-05-15
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
```

I thought so ,and you have dual boot. I guess I know where the problem is and how to solve it.
I've got same card and had same issues.

1. Your (my) ethernet card sometimes does not switch off during rebooting Windows.

From archwiki
> Users with Realtek 8168 8169 8101 8111(C) based NICs (cards / and 
on-board) may notice a problem where the NIC seems to be disabled on 
boot and has no Link light. This can usually be found on a dual boot 
system where Windows is also installed. It seems that using the official
 Realtek drivers (dated anything after May 2007) under Windows is the 
cause. These newer drivers disable the Wake-On-LAN feature by disabling 
the NIC at Windows shutdown time, where it will remain disabled until 
the next time Windows boots. You will be able to notice if this problem 
is affecting you if the Link light remains off until Windows boots up; 
during Windows shutdown the Link light will switch off. Normal operation
 should be that the link light is always on as long as the system is on,
 even during POST. This problem will also affect other operating systems
 without newer drivers (eg. Live CDs).

Solution. Do not reboot Windows if you want to log in to Ubuntu.
Do these steps:
a. In Windows instead of clicking "reboot", click "shut down the system."
b. Wait 5 sec after computer is shutdown
c. Log in to Ubuntu and the problem will be solved.
P.S. It is safe to reboot Ubuntu and log in to Windows - the ethernet card will be working. But if you would like to log in to Ubuntu again, then also do not reboot Ubuntu, but shut down the system, wait 5 sec and log in again.

It is the lame, but the easiest way.


2. Sometimes Realtek 8168 has driver problems in kernel 5.4 and/or 5.8. Means the connection is lost or unstable.
I solved the problem with installing external driver for that card.
I did things which are described here
[https://ubuntuforums.org/showthread.php?t=2456227&p=14012451#post14012451](https://ubuntuforums.org/showthread.php?t=2456227&p=14012451#post14012451)

---

### Post by ronjjjg8885 on 2021-05-16
ok people
but i'm not sure that my question about buying a new network card has been answered. will it work in your opinion with another card which isn't built in card?
thank you for the help
next time it will happen i will try to shut down windows instead of rebooting.
LOVE!!!

---

### Post by TheFu on 2021-05-16
> **ronjjjg8885 said:**
>  
but i'm not sure that my question about buying a new network card has been answered. will it work in your opinion with another card which isn't built in card?

If the issue isn't with the NIC, then no, a new card won't help. It could be the switch, cables, something else.  

If the issue is with the NIC, then disable to built-in NIC through the BIOS and use the addon NIC. Don't let them be connected to the same physical subnet.

In enterprises, it is common to have 6 NIC ports on a server and to bond 2 ports each onto 1 subnet thanks to some ethernet standards for redundancy and failover that enterprise switches support. Cheap home switches usually don't support those protocols until we start buying "managed switches." 
I have 3 ports on some of my "desktop" servers, but that's because well-supported NICs don't fail often enough to need redundancy.  These are normal desktop machines, just used as servers. Much lower power use, much quieter, but still very capable to run 10-30 VMs. The different ports are for connections to different physical networks.  I don't trust vlans for security. If I did, I could have 1 NIC, 3 IPs, and VLAN capable networking gear to make it all logical, not physical, network design.

So, the answer is "it depends."  There have been suggestions made which appear to be ignored. OTOH, having a quality NIC can be useful for all sorts of reasons, but nobody here knows whether it will help or not. Only you can decide.  My rule is simple. Avoid Realtek and I wouldn't buy a Marvell for a replacement.

---

### Post by ronjjjg8885 on 2021-06-05
i will have to check your suggestions because i've a problem again after doing a partial upgrade.

---

### Post by kurt18947 on 2021-06-06
If the above suggestions don't help, you could try a USB ethernet dongle. I have one because I was concerned about internal NIC support on a new motherboard. I did try it and it worked as expected. I find it handy having standby hardware, it's the simplest way for me to check whether hardware is being problematic.

---

