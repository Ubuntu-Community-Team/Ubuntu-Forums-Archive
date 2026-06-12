---
title: "System Hangs On Any Type Of Large Download"
date: 2017-07-20
forum: General Help
---

### Post by SBTlauien on 2017-07-20
I have Ubuntu 16.04.2 running on my Surface Pro 3.  I have installed a lot of programs since installing it and had no problems.  At this point, when I try to download anything (from BitTorrent or even "apt-get install"), my system completely hangs.  I only have 4GB of RAM but I don't think that's the issue since I was able to download fine before.  It doesn't hang if I'm not doing a big download.  It is specifically on large downloads.

After searching I came across the thread below and I edited the file and ran the command, but I still get a complete system hang when downloading. 

 [https://askubuntu.com/questions/397249/system-freezes-unresponsive-unusable-when-copying-large-file-to-usb](https://askubuntu.com/questions/397249/system-freezes-unresponsive-unusable-when-copying-large-file-to-usb)

  I ran a disk check using Badlocks while in a live session and it said that my disk was 100% okay.  What could be causing this and how can I fix it?

---

### Post by Bashing-om on 2017-07-20
SBTlauien; Hey ... A thought .

Disk space ??

What shows:
```

df -h
df -i
du -shx /*

```

[INDENT][INDENT]maybe this
[INDENT][INDENT]could be that
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by SBTlauien on 2017-07-21
Nope, I have over 100GB free.

Although I was just able to install a large program.

After I edited the file from the link above and running the command from the link above, I didn't restart.  I immediately tried to download something and Ubuntu hung forcing me to hold in my power key to turn off the device.  Could it be that it works because I have since restarted my system?

---

### Post by Bashing-om on 2017-07-21
SBTlauien; Welp :

> 
Could it be that it works because I have since restarted my system?

A re-boot can and does re-align the system; resolving config issues - sometimes.

However, my concern now is directed at :
> 
 forcing me to hold in my power key to turn off the device.

Such an action can leave the file system in an inconsistent state.
I always run a file system check ANY time there a loss of power to the system while in operation.
A couple of ways to run this file system check with systemd.
I have the preference for:
[https://wiki.archlinux.org/index.php/fsck](https://wiki.archlinux.org/index.php/fsck)
where one inserts the file system check at boot time by passing " fsck.mode=force " to the kernel from grub's boot command line .
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key (MBR) or spam the escape key (EFI)-> grub menu> Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-4.4.0-83-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term " fsck.mode=force " -without the quotes-; ctl+x to continue the boot process.

Be aware :
> 
Nope, I have over 100GB free.

At large has no relation to particular partitions - say for instance the /boot partition.
which is why I suggested to "look" with the 'df' commands.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by BenginM on 2017-07-21
Salutations, please follow Bashing-om ..

paste the output of inside a ```
 tag like so.  

[CODE]
df -h
df -i
du -shx /*

```

what are you using to download these large files , also connection is through wired or wifi !

does the system freezes/hangs using wget :


```


wget -c -o http://mirrors.mit.edu/ubuntu-cdimage/daily-live/20170719/artful-desktop-amd64.iso


```

---

### Post by SBTlauien on 2017-08-10
So this problem is back.  The system even hangs if I try to clone a repository using "git clone".  It's a complete freeze, no escape.  The connection is wireless.  I have no idea what could be causing this.  No error log, nothing.

---

### Post by Autodave on 2017-08-10
Please post the output of the commands that Bashing-Om asked for. If you want further help, you need to start there.

---

### Post by VMC on 2017-08-10
Mine will hang if IPV6 is allowed:
[https://askubuntu.com/questions/620317/apt-get-update-stuck-connecting-to-security-ubuntu-com](https://askubuntu.com/questions/620317/apt-get-update-stuck-connecting-to-security-ubuntu-com)

---

### Post by SBTlauien on 2017-08-17
df -h
```

Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           386M  6.5M  380M   2% /run
/dev/sda2       113G   19G   89G  18% /
tmpfs           1.9G  308K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1       511M  4.9M  507M   1% /boot/efi
tmpfs           386M   76K  386M   1% /run/user/1000
/dev/sdb1       7.4G   32K  7.4G   1% /media/user/6333-6332

```

df -i
```

Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            488308    582  487726    1% /dev
tmpfs           493637    853  492784    1% /run
/dev/sda2      7528448 504853 7023595    7% /
tmpfs           493637     20  493617    1% /dev/shm
tmpfs           493637      5  493632    1% /run/lock
tmpfs           493637     16  493621    1% /sys/fs/cgroup
/dev/sda1            0      0       0     - /boot/efi
tmpfs           493637     35  493602    1% /run/user/1000
/dev/sdb1            0      0       0     - /media/user/6333-6332

```

du -shx /*
[https://paste.ubuntu.com/25336215/](https://paste.ubuntu.com/25336215/)

---

### Post by SBTlauien on 2017-08-17
> **VMC said:**
> Mine will hang if IPV6 is allowed:
[https://askubuntu.com/questions/620317/apt-get-update-stuck-connecting-to-security-ubuntu-com](https://askubuntu.com/questions/620317/apt-get-update-stuck-connecting-to-security-ubuntu-com)

My whole system is hanging, causing me to hold in the power button to turn it off to restart.

---

### Post by BenginM on 2017-08-18
you mentioned the connection was on wireless , is the wifi connection directly to the Access Point or through a wifi extender ..!

 does the system hangs on wired ethernet ..? try downloadin' large files with Ethernet ..

---

### Post by SBTlauien on 2017-08-19
> **BenginM said:**
> you mentioned the connection was on wireless , is the wifi connection directly to the Access Point or through a wifi extender ..!   does the system hangs on wired ethernet ..? try downloadin' large files with Ethernet ..  It happens when I connect to a public wifi hotspot and when I connect to my phones hotspot.  This is all on my Surface Pro 3, so there is no wired ethernet, only wireless ethernet.

---

### Post by BenginM on 2017-08-20
is there a bandwidth limit on the *cellular data ! you may need to connect to a wifi access point or through ethernet cable -Not-hotspot to determine if it's a wireless card driver issue ..* what wireless card is it and which driver in use.. in a terminal run: $ inxi -Nn

---

### Post by SBTlauien on 2017-08-20
I don't have that program and don't want to risk having a crash again without trying something first, so I ran the commnad below.

lspci | awk '/[Nn]et/ {print $1}' | xargs -i% lspci -ks %
```

01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8897 [AVASTAR] 802.11ac Wireless
    Subsystem: SafeNet (wrong ID) 88W8897 [AVASTAR] 802.11ac Wireless
    Kernel driver in use: mwifiex_pcie
    Kernel modules: mwifiex_pcie



```

---

### Post by BenginM on 2017-08-20
disconnect from the wifi hotspot , 

in a terminal run :
tail -f /var/log/syslog

then connect to your phone's hotspot , now try to download a file with wget ,, watch the logs in the terminal look for lines with mwifiex ..  if the system hangs again , then i have a hunch that the driver is crashing .. so you may want to look for a crash logs in kern.log.1 under /var/log/

---

