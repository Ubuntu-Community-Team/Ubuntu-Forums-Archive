---
title: "syslog: Assuming drive cache: write through - bla bla - hassle me"
date: 2013-04-10
forum: General Help
---

### Post by rnerwein on 2013-04-10
hello
can anybody help me to get rid of the messages (see next sentence) im my /var/log/* .
got 100000 of them since about 6 month.
the messages are:
Apr 10 10:04:54 tschang kernel: [ 7300.334798] sd 13:0:0:0: [sdh] Asking for cache data failed
Apr 10 10:04:54 tschang kernel: [ 7300.334804] sd 13:0:0:0: [sdh] Assuming drive cache: write through
Apr 10 10:04:54 tschang kernel: [ 7300.460039] usb 2-5: reset high-speed USB dev

but the devices change all the time. depents on what i have connected. (sdc, sdg, sdh).
oh yes i always unmount my mountpoints /media. by the side 99% i am only using the terminal (for sure super-user when using unmount !)
may be the is a error in reasoning - why - in my /var/log/dmesg i can find:

[    4.057755]  sdg: sdg1 sdg2 < sdg5 sdg6 sdg7 sdg8 sdg9 >
[    4.064505] sd 11:0:0:0: [sdg] No Caching mode page present
[    4.064507] sd 11:0:0:0: [sdg] Assuming drive cache: write through
[    4.064509] sd 11:0:0:0: [sdg] Attached SCSI disk
[    4.780644] scsi 12:0:0:0: [COLOR=#ff0000]CD-ROM            FRITZ!   WLAN selfinstall 1.00 PQ: 0 ANSI: 0 CCS[/COLOR]
[    4.782007] sr2: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    4.782105] sr 12:0:0:0:[COLOR=#ff0000] Attached scsi CD-ROM sr2[/COLOR]
[    4.782177] sr 12:0:0:0: [COLOR=#ff0000]Attached scsi generic sg9 type 5[/COLOR]
[   10.138377] usb 2-4.2: USB disconnect, device number 6
[   11.360631] usb 2-4.2: new high-speed USB device number 7 using ehci_hcd

may be there is some relation (but the messages there is sdh shown). 
for sure - there is no problem with my /etc/fstab. even mount don't show me /dev/sdh. even fdisk -l or lsblk and so on -> nothing
where ist the total recall of my box - help !
oh - by the side i know uninx/linux very well.
for a hint i'll be much obliged.
ciao
is it possible that the CD-drive can the guarantor of my problem ? this CD-drive is my Wifi usb stick ;-)  but works fine for a CD on the net !

---

