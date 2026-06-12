---
title: "Ubuntu 16 not detecting usb"
date: 2018-11-18
forum: General Help
---

### Post by nuey on 2018-11-18
I know this type of question has been posted ,but not of the answers have addressed my situation.

When I plug a usb in, I do not see it in the Disks application.  Nothing seems to happen at all.
After looking at some previous posts on this topic a did the following:

before inserting usb:
```

sudo lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

after inserting usb:
OUTPUT:
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


There is no change before and after inserting the usb (one which is detected on an apple computer).

I have run various other commands
```

sudo modprobe-usb-storage

``` which produced no ouput, and 
```

sudo fdisk -l

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 472260607 472258560 225.2G 83 Linux
/dev/sda2       472262654 488396799  16134146   7.7G  5 Extended
/dev/sda5       472262656 488396799  16134144   7.7G 82 Linux swap / Solaris

```

and finally 
```

lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0 225.2G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.7G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  
loop0    7:0    0  87.9M  1 loop /snap/core/5662
loop1    7:1    0  87.9M  1 loop /snap/core/5548
loop2    7:2    0 193.1M  1 loop /snap/acestreamplayer/7
loop3    7:3    0   3.3M  1 loop /snap/udisks2/100
loop4    7:4    0  87.9M  1 loop /snap/core/5742

```


and while I do not understand the output, they do not change before and after inserting the usb.

I have used usbs maybe 6 months ago without issue, so I am not sure what has changed.
The only thing I can think of is that I installed Ace Stream player in September, though I don't
know why that would effect anything.

Any help would be greatly appreciated.

---

### Post by 23dornot23d on 2018-11-18
You could try installing mountpy

[B]$ sudo apt install mountpy

$ sudo mountpy[/B]

See if the usb then picks up - is it a usb that lights up - and if so does it light up at all when inserted - could be a bad usb port - that is all I can think of if
it does not light up and detect it ........... over time they can get damaged.

---

### Post by oldfred on 2018-11-18
Many new systems have settings in UEFI for USB ports. Both enable and allow boot. Sometimes even mouse & keyboard may not be shown.
When UEFI Secure boot is on, booting from USB port is not allowed, normally, as not secure. You have to specifically enable it. But even if Secure Boot is off, you may still have to enable USB ports.

---

### Post by ajgreeny on 2018-11-18
Without the usb plugged in run command ```
dmesg | tail
```
Now plug in the usb and run the command again to see any new last lines appear which may give us some better clues.

---

