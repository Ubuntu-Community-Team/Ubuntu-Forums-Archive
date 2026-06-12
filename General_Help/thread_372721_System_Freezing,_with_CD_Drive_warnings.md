---
title: "System Freezing, with CD Drive warnings"
date: 2007-02-28
forum: General Help
---

### Post by jeduan on 2007-02-28
I have been using Ubuntu since Dapper with no major problems at all, however, since yesterday the system has been freezing completely. It has happened at least 4 times.
At the moment of freezing, only firefox was open in the system.

Before one of the crashes I managed to get to the terminal, I was flooded with a bunch of 
```
hdc: drive not ready for command

```

So, I think the problem lies on the DVD drive.
here is the output for dmesg | grep hdc
```
jeduan@luau:~$ dmesg | grep hdc
[17179574.220000]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
[17179576.000000] hdc: MATSHITAUJ-840D, ATAPI CD/DVD-ROM drive
[17179576.456000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.692000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179578.692000] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[17179578.696000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179578.696000] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[17179605.400000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179605.400000] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[17179706.852000] hdc: status timeout: status=0xa0 { Busy }
[17179706.852000] hdc: DMA disabled
[17179706.852000] hdc: drive not ready for command
[17179728.116000] hdc: ATAPI reset complete
[17180205.968000] hdc: status error: status=0x00 { }
[17180205.968000] hdc: status error: status=0x00 { }
[17180205.968000] hdc: status error: status=0x00 { }
[17180205.968000] hdc: status error: status=0x00 { }
[17180206.016000] hdc: ATAPI reset complete
[17180206.016000] hdc: status error: status=0x00 { }
[17180206.016000] hdc: status error: status=0x00 { }
[17180206.016000] hdc: status error: status=0x00 { }
[17180206.016000] hdc: status error: status=0x00 { }
[17180206.064000] hdc: ATAPI reset complete
[17180206.064000] hdc: status error: status=0x00 { }
[17180206.064000] hdc: status error: status=0x00 { }
[17180206.064000] hdc: status error: status=0x00 { }
[17180206.064000] hdc: status error: status=0x00 { }
[17180206.064000] hdc: status error: status=0x00 { }
[17180206.256000] hdc: ATAPI reset complete
[17180206.264000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[17180206.264000] hdc: drive not ready for command
[17180206.264000] hdc: request sense failure: status=0x51 { DriveReady SeekComplete Error }
[17180206.264000] hdc: request sense failure: error=0x50 { LastFailedSense=0x05 }
[17181045.380000] hdc: tray open
[17181045.380000] end_request: I/O error, dev hdc, sector 0
[17181045.380000] Buffer I/O error on device hdc, logical block 0
[17181045.384000] hdc: tray open
[17181045.384000] end_request: I/O error, dev hdc, sector 4
[17181045.384000] Buffer I/O error on device hdc, logical block 1
[17181045.384000] hdc: tray open
[17181045.384000] end_request: I/O error, dev hdc, sector 8
[17181045.384000] Buffer I/O error on device hdc, logical block 2
[17181045.384000] hdc: tray open
[17181045.384000] end_request: I/O error, dev hdc, sector 12
[17181045.384000] Buffer I/O error on device hdc, logical block 3
[17181045.384000] hdc: tray open
[17181045.384000] end_request: I/O error, dev hdc, sector 16
[17181045.384000] Buffer I/O error on device hdc, logical block 4
[17181045.388000] hdc: tray open
[17181045.388000] end_request: I/O error, dev hdc, sector 20
[17181045.388000] Buffer I/O error on device hdc, logical block 5
[17181045.388000] hdc: tray open
[17181045.388000] end_request: I/O error, dev hdc, sector 24
[17181045.388000] Buffer I/O error on device hdc, logical block 6
[17181045.388000] hdc: tray open
[17181045.388000] end_request: I/O error, dev hdc, sector 28
[17181045.388000] Buffer I/O error on device hdc, logical block 7
[17181045.388000] hdc: tray open
[17181045.388000] end_request: I/O error, dev hdc, sector 0
[17181045.388000] Buffer I/O error on device hdc, logical block 0
[17181045.392000] hdc: tray open
[17181045.392000] end_request: I/O error, dev hdc, sector 4
[17181045.392000] Buffer I/O error on device hdc, logical block 1
[17181045.392000] hdc: tray open
[17181045.392000] end_request: I/O error, dev hdc, sector 0
[17181045.392000] hdc: tray open
[17181045.392000] end_request: I/O error, dev hdc, sector 4
[17181045.392000] hdc: tray open
[17181045.392000] end_request: I/O error, dev hdc, sector 0
[17181045.396000] hdc: tray open
[17181045.396000] end_request: I/O error, dev hdc, sector 4

```

I'm on Ubuntu 6.10, with a 2.6.17-11-generic kernel on a BenQ JoyBook 2100 laptop.

I hope anyone will be able to shed light on this.

---

