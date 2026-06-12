---
title: "Slow Booting Ubuntu 14.04.02 LTS 32 Bits"
date: 2015-05-02
forum: General Help
---

### Post by SebasOut on 2015-05-02
****Problem****:

It takes to much time to start Ubuntu. (7 minutes after the Grub Screen)

Ubuntu 14.04.02 LTS 32 Bits

****Problem Description****

1) Turn on the PC

2) 1 minute after the Grub Screen appears 

3) Once selected Ubuntu as the Operative System it start the process of loading the OS.

4) 7 minutes later, the Login screen of Ubuntu appears.

5) Once Ubuntu starts, everything works 100%


****Computer Description****

Laptop ACER Aspire 5542-5770

Core: AMD Turion II X2 M500 – 2.2GHz, 1MB L2 Cache

Video Card: ATI Radeon HD 4200 Graphics up to 1919 MB HyperMemory

Memory Ram: 4 Gb

Hard Drive: 320 Gb (sdb)

Ubuntu is not installed in the Laptop hard drive, is installed in a portable Hard Drive connected by USB. 

****Portatil Hard Drive Toshiba 500 Gb (sda)****

/dev/sda1 – ext2 - /boot – 2 Gb

/dev/sda2 – ext4 - / - 50 Gb

/dev/sda3 – extended

    /dev/sda5 – linux-swap – 2 Gb

    /dev/sda6 – ext4 - /home – 172 Gb

Free – 240 Gb

The records from booting are useless. All the records starts 30 seconds before Ubuntu starts, meaning that they start 6 minutes and 30 seconds after the Grub screen.

****Solutions Tested**** (Not worked)

/etc/default/grub

I probe modifying the next line: GRUB_CMDLINE_LINUX_DEFAULT=""

Using all this parameters:
splash – quiet – noapic – nolapic – acpi=noirq

None of this make a change at all.

****I am also sending all the reports, and it must be taken into account that I turned on the computer at 22:00 hours.****

Logs:

[https://drive.google.com/open?id=15XOD-B1l85n-1C6Qh10NjQHPx5uUe4m586FKNoyV7jA&authuser=0](https://drive.google.com/open?id=15XOD-B1l85n-1C6Qh10NjQHPx5uUe4m586FKNoyV7jA&authuser=0)

Bootchart Image:

[https://drive.google.com/open?id=0B9p-rpoU17qNX0F1Q25LbU1yQWM&authuser=0](https://drive.google.com/open?id=0B9p-rpoU17qNX0F1Q25LbU1yQWM&authuser=0)

---

### Post by sudodus on 2015-05-03
Welcome to the Ubuntu Forums :-)

I suggest that you try another flavour of Ubuntu. The flavours are developed by the Ubuntu community. They have the same linux engine and basic program packages under the hood, but the desktop environment (the graphical user interfaces) are different. Some of the flavours have lighter desktop environments than standard Ubuntu.

Xubuntu is medium light with the desktop environment XFCE.
Lubuntu is ultra light with the desktop environment LXDE.
Ubuntu Mate is medium light with he desktop environment MATE (a fork of gnome 2).
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL] 				

When you have found something that works better, you can start tweaking it, maybe check if there is a working proprietary driver to your graphics card and your wifi chip.

---

### Post by coffeecat on 2015-05-03
Welcome to the forum. This sounds like a request for help, therefore not suited for the Ubuntu, Linux and OS Chat section, so...

*Thread moved to **General Help**.*

---

### Post by SebasOut on 2015-05-04
_**sudodus**_:


FIrst of all thanks for your answer. I will consider the option of try another flavour of Ubuntu very seriously.


But, I think Ubuntu is not the problem. In this computer (which should run Ubuntu and a lot more), I installed Ubunutu once and everything was going perfect, but the main problem was that i did not create a boot sector in the USB Hard Disc, meaning that I changed my MRB in my computer without meaning, and when I plug my Portable Hard Drive in another computer it could not run Ubuntu. Now, I actually did everything right with the partitions and the problem is another one.


I am really looking for an answer a little bit more specific for the kind of problem I am having.

But thanks anyway.

_**coffecat**_:

Really sorry, I actually didn't know where I should post this problem. Thanks for moving the post from sections!!

---

### Post by sudodus on 2015-05-05
> **SebasOut said:**
> _**...**_
I am really looking for an answer a little bit more specific for the kind of problem I am having.

But thanks anyway.
...

Please ask more specific questions (one each time), and I will try to answer more specifically. And I hope other people will chip in and give tips and advice relevant to each of your questions :-)

---

### Post by SebasOut on 2015-05-05
I mean that the problem I got is not because my computer isn't good enough, it's because something else.


I really apreciate your answer sudodus, but I am looking for an answer from my main problem (The 7 minutes delay to start Ubuntu) that could maybe solve my problem, and not to try avoiding the problem by installing another flavour of Ubuntu.


For instance, it would be great if there is some sugestion that i could do to really see whats going on in those 7 minutues after grub and before the login screen. At this moment, in the grub configuration i got GRUB_CMDLINE_LINUX_DEFAULT="" without any parameters (I took away quiet and splash), and i can't see whats going on in that 7 minutes.

Thanks for your patience!!

---

### Post by oldfred on 2015-05-05
With 14.04 you can look at the log files. Often first to review is dmesg. You can use log file viewer or system logs. Or directly open it:
       gksudo gedit /var/log/dmesg

It is long, you do not need to post all, but any errors, warnings or the one's with long time stamps between entries. Some may show a warning or error and retry and then be successful. 

I boot with SSD and log file says last entry is 5.6, this is my longest entry and hard drive data partition takes a full second to mount.
```

[    4.323062] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    5.373222] EXT4-fs (sdb4): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by SebasOut on 2015-05-22
If I open a console and write the command: $ dmesg | tail

The result is this:
[ 1084.399308] raid6: int32x8    635 MB/s
[ 1084.399310] raid6: using algorithm mmxx2 (3443 MB/s)
[ 1084.399312] raid6: using intx1 recovery algorithm
[ 1084.399642] Request for unknown module key 'Magrathea: Glacier signing key: 6845910c6be1e6ebafedc62a4add930d5054a027' err -11
[ 1084.399916] xor: measuring software checksum speed
[ 1084.439324]    pIII_sse  :  8551.000 MB/sec
[ 1084.479373]    prefetch64-sse:  8748.000 MB/sec
[ 1084.479376] xor: using function: prefetch64-sse (8748.000 MB/sec)
[ 1084.480918] Request for unknown module key 'Magrathea: Glacier signing key: 6845910c6be1e6ebafedc62a4add930d5054a027' err -11
[ 1084.490130] Btrfs loaded

Could you help me please? Dont know what this means.

Also, I will add some lines before of those

[   37.027710] init: cups main process (960) killed by HUP signal
[   37.027721] init: cups main process ended, respawning
[   38.635521] init: samba-ad-dc main process (1028) terminated with status 1
[   38.936744] tg3 0000:03:00.0: irq 42 for MSI/MSI-X
[   39.043404] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.376993] init: plymouth-upstart-bridge main process ended, respawning
[   51.098586] ata1: exception Emask 0x40 SAct 0x0 SErr 0x800 action 0x7
[   51.098594] ata1: SError: { HostInt }
[   51.098600] ata1: hard resetting link
[   51.597965] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   51.600339] ata1.00: configured for UDMA/133
[   51.613918] ata1: EH complete
[   66.063845] audit_printk_skb: 132 callbacks suppressed
[   66.063851] audit: type=1400 audit(1432325266.393:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1715 comm="apparmor_parser"
[   66.063863] audit: type=1400 audit(1432325266.393:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1715 comm="apparmor_parser"
[   66.064422] audit: type=1400 audit(1432325266.393:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1715 comm="apparmor_parser"
[  876.687524] audit: type=1400 audit(1432326076.361:71): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3271 comm="apparmor_parser"
[  876.687539] audit: type=1400 audit(1432326076.361:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3271 comm="apparmor_parser"
[  876.688333] audit: type=1400 audit(1432326076.361:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3271 comm="apparmor_parser"

---

### Post by oldfred on 2015-05-22
Are you using RAID and btrfs? Or not a standard install?

This seems to be a major time loss:
```
[   66.064422] audit: type=1400 audit(1432325266.393:70):  apparmor="STATUS" operation="profile_replace" profile="unconfined"  name="/usr/sbin/cupsd" pid=1715 comm="apparmor_parser"
[  876.687524] audit: type=1400 audit(1432326076.361:71):  apparmor="STATUS" operation="profile_replace" profile="unconfined"  name="/usr/lib/cups/backend/cups-pdf" pid=3271 comm="apparmor_parser"
```

But I do not know what unconfined means. But what printer are you using, as it seems related to cups.

---

### Post by Kpenguin on 2015-05-22
The slow boot problem could be with the external HDD. What do you plug it into? A USB port? If so, is it 2.0 or 3.0?
I'm not an expert, but this is the first thing that would come to mind. :)

---

### Post by SebasOut on 2015-08-19
Sorry, for the delay in the answer.


It's not a USB speed problem, because in other computers it boots in less than one minute. Is a real problem of my computer, and my main hypotesis is related with the Card Reader SD that this computer got's. (Other computers = Older computers with also USB 2.0).


I couldn't find any answer to this problem in all this months and not even a clue of what could really be, only my hypotesis with no solution.

---

### Post by sudodus on 2015-08-20
It may work better with another flavour of Ubuntu for example Lubuntu with a light desktop environment.

It may also work better with another version of Ubuntu (14.04.1 LTS, 14.04.3 LTS, 15.04 or even 12.04.1 LTS) which has a different kernel and different hardware drivers (different from 14.04.2 LTS). Notice that Lubuntu 12.04 had no long time support so it has passed end of life, but you can use LXLE which supports a community re-spin based on Ubuntu 12.04 LTS until April 2017.

-o-

The problem could be what you suspect, that the system is testing drivers for the card reader, or something related, the floppy drive. One solution might be to blacklist the floppy drive, because you won't use it anyway.

See [AskUbuntu: How to completely disable floppy in Ubuntu 14.04?](https://askubuntu.com/questions/457970/how-to-completely-disable-floppy-in-ubuntu-14-04)

> Problem solved! Found the solution on Ubuntu 14.04 in terminal run:

```
echo "blacklist floppy" | sudo tee /etc/modprobe.d/blacklist-floppy.conf
sudo rmmod floppy
sudo update-initramfs -u
```

works right away.

---

