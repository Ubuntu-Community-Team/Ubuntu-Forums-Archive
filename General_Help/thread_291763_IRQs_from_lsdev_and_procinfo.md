---
title: "IRQs from lsdev and procinfo"
date: 2006-11-02
forum: General Help
---

### Post by mayonaise15 on 2006-11-02
I'm doing some homework for my computer hardware class.  I need to find out the IRQ assignments for at least channels 0-15.  I'm only getting a few from lsdev and procinfo looks like it is showing me a map.  Can somebody tell me if there is a more detailed way to show IRQ assignments?

lsdev:
```
Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:0a.1                 0600-063f 0700-073f
0000:00:0d.0                 ffa0-ffaf
0000:00:0e.0                 e000-e00f e080-e083 e400-e407 e480-e483 e800-e807
0000:00:14.0                 dc00-dc07
acpi                      9 
ACPI                         0500-0503 0504-0505 0508-050b 0520-0527 5010-5015
cascade             4       
dma                          0080-008f
dma1                         0000-001f
dma2                         00c0-00df
ehci_hcd:usb2           233 
eth0                    217 
forcedeth                      dc00-dc07
fpu                          00f0-00ff
ide0                     14  01f0-01f7 03f6-03f6   ffa0-ffa7
ide1                     15  0170-0177 0376-0376   ffa8-ffaf
Intel                   209 
keyboard                     0060-006f
motherboard                  2000-207f 2080-20ff
nvidia                   50 
ohci_hcd:usb1           225 
parport0            3     7  0378-037a 037b-037f 0778-077a
PCI                          0cf8-0cff
pic1                         0020-0021
pic2                         00a0-00a1
pnp                          0290-0297
rtc                       8  0070-0077
sata_nv                        e000-e00f   e080-e083   e400-e407   e480-e483   e800-e807
serial                       03f8-03ff
timer                     0 
timer0                       0040-0043
timer1                       0050-0053
vga+                         03c0-03df

```

procinfo:
```
Linux 2.6.17-10-generic (root@vernadsky) (gcc [can't parse]) #???  1CPU [Leslie]

Memory:      Total        Used        Free      Shared     Buffers      
Mem:       1035484     1008864       26620           0       60668
Swap:      2321352       17688     2303664

Bootup: Wed Nov  1 21:48:42 2006    Load average: 0.44 0.26 0.20 1/166 7947

user  :       0:57:02.08   4.6%  page in :  1381455  disk 1:    52807r  108386w
nice  :       0:08:07.77   0.7%  page out:  2110962  disk 2:      105r       0w
system:       0:05:08.80   0.4%  page act:   382227  disk 3:       14r       0w
IOwait:       0:02:50.61   0.2%  page dea:   135734  disk 4:       10r       0w
hw irq:       0:01:00.95   0.1%  page flt:  7888271
sw irq:       0:04:36.51   0.4%  swap in :       11
idle  :      19:22:42.27  93.7%  swap out:     4422
uptime:      20:41:30.96         context : 54501899

irq  0:  18620565 timer                 irq 11:         1                      
irq  1:         3                       irq 12:         3                      
irq  4:         2                       irq 14:    161324 ide0                 
irq  5:         1                       irq 15:    888785 ide1                 
irq  6:         5                       irq 50:   4622259 nvidia               
irq  7:         1 parport0 [3]          irq209:   1306591 libata, HDA Intel    
irq  8:         3 rtc                   irq217:   8853169 eth0                 
irq  9:         0 acpi                  irq225:    269862 ohci_hcd:usb1        
irq 10:         1                       irq233:    400981 ehci_hcd:usb2        


```

---

### Post by mayonaise15 on 2006-11-03
bump

---

