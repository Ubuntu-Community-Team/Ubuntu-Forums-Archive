---
title: "Ubuntu 20.04 random crashes"
date: 2022-02-16
forum: General Help
---

### Post by pleasant-pineapple-7 on 2022-02-16
[COLOR=#1A1A1B][FONT=&amp]When I first installed ubuntu 6 months ago, I didn't have any huge issues. But my computer has started to randomly freeze in which cursor and keyboard input stops and I am forced to reboot. This originally happend sporadically, but is now at least once a day. I have not related the crashes to any particular activity. I frequently use RStudio and Chrome.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I have never had any crashes or trouble when I boot into Windows, so I have felt it is more likely a software problem with linux or grub than it is with computer hardware. However I have no idea where to start troubleshooting.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I was running kernel 5.13.0-28-generic, and tried switchinig to both 5.13.9-27 as well as a 5.10 kernel to see if that was somehow related, but have still been crashing while using these as well.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I have a dual boot Windows 10 / Ubuntu 20.04 system with intel i7, 16GB RAM, 100ish GB HD and 16GB swap space. Ubuntu is installed on a separate 256GB SSD than Windows 10 which is on its own 500GB HD. Both OS have access to a 4TB HDD which is NFTS-formatted.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Here are a bunch of logs and components I use in case it is helpful:[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp][https://linux-hardware.org/?probe=bd4ee9e124](https://linux-hardware.org/?probe=bd4ee9e124)[/FONT][/COLOR]

---

### Post by TheFu on 2022-02-16
Check the logs. Look for errors. There are many ways to read/search the log files on a system.

I've had stability issues with mis-matched RAM sticks on a Ryzen system.  I bought 16G of RAM initially, then added another 16G of the same SKU/vendor/model RAM. This wasn't a "matched quad".  The solution was to set slower RAM speed in the BIOS until stability improved.  I've been installing new BIOSes every 6 months, or so, and most improved stability, to a point.  It has been stable since the last group of crashes last fall - about the last 4 months, perfectly stable.  The RAM issues were showing up in the logs, clearly, as kmem/swap problems.  I'm running 3200Mhz RAM at ... 
```
$ sudo inxi -m
Memory:    Used/Total: 17932.9/32096.8MB
           Array-1 capacity: 128 GB devices: 4 EC: None
           Device-1: DIMM_A1 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-2: DIMM_A2 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-3: DIMM_B1 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-4: DIMM_B2 size: 8 GB speed: 2666 MT/s type: DDR4
```
On a newer Ryzen, same board, different CPU generation, I've not had any stability issues.
```
$ sudo inxi -m
Memory:    Used/Total: 3513.6/15112.3MB
           Array-1 capacity: 128 GB devices: 4 EC: None
           Device-1: DIMM_A1 size: No Module Installed type: N/A
           Device-2: DIMM_A2 size: 8 GB speed: 3200 MT/s type: DDR4
           Device-3: DIMM_B1 size: No Module Installed type: N/A
           Device-4: DIMM_B2 size: 8 GB speed: 3200 MT/s type: DDR4
```
Running at full speed. Both boards have the same BIOS installed.

If your system isn't Ryzen, I don't have a clue. Looking through unfiltered logs is too much like .... "work."

---

