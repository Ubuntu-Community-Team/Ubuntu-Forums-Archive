---
title: "USB pain in the ***"
date: 2007-12-05
forum: General Help
---

### Post by cisforcojo on 2007-12-05
Hey all, 

I just purchased a Chinese electronic dictionary that connects through USB. Whenever I connect it, it mounts 2 places, the internal flash disk and my 1GB disk (SD?) disk. Those pop up on my desktop as 'disk' and 'Kingston'. I copied 2 files to 'disk' at the same time and did not have a problem. Tried copying another file and it just hung on 'Preparing to copy...' I tried several more times, I could copy again (didn't try two times) but this time when I tried to eject, both 'disk' and 'Kingston' never finished writing the files (the file is only 16 MB). 

Any ideas???????? I dunno what to do.

Here is the output of my lsmod and dmesg (without any file xfers):

```
cojones@tipping-point:~$ lsmod |grep hcd
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  7 usb_storage,libusual,xpad,usbhid,ehci_hcd,uhci_hcd

```
 
```
[  175.148000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  175.320000] usb 3-1: configuration #1 chosen from 1 choice
[  175.720000] usbcore: registered new interface driver libusual
[  175.852000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  175.852000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  175.860000] Initializing USB Mass Storage driver...
[  175.864000] scsi2 : SCSI emulation for USB Mass Storage devices
[  175.864000] usb-storage: device found at 2
[  175.864000] usb-storage: waiting for device to settle before scanning
[  175.864000] usbcore: registered new interface driver usb-storage
[  175.864000] USB Mass Storage support registered.
[  180.864000] usb-storage: device scan complete
[  180.956000] scsi 2:0:0:0: Direct-Access     BBK                       0100 PQ: 0 ANSI: 0 CCS
[  180.968000] sd 2:0:0:0: [sdb] 3005704 512-byte hardware sectors (1539 MB)
[  180.972000] sd 2:0:0:0: [sdb] Write Protect is off
[  180.972000] sd 2:0:0:0: [sdb] Mode Sense: 00 2a 00 00
[  180.972000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  180.984000] sd 2:0:0:0: [sdb] 3005704 512-byte hardware sectors (1539 MB)
[  180.988000] sd 2:0:0:0: [sdb] Write Protect is off
[  180.988000] sd 2:0:0:0: [sdb] Mode Sense: 00 2a 00 00
[  180.988000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  180.988000]  sdb: sdb1 sdb2
[  180.996000] sd 2:0:0:0: [sdb] Attached SCSI disk
[  180.996000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  341.980000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  342.532000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  343.084000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  343.636000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  344.192000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  344.748000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  344.904000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  344.904000] end_request: I/O error, dev sdb, sector 826912
[  345.284000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  345.820000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  346.356000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  346.892000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  347.428000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  347.964000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  348.120000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  348.120000] end_request: I/O error, dev sdb, sector 827152
[  348.496000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  349.028000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  349.560000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  350.092000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  350.624000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  351.156000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  351.312000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  351.312000] end_request: I/O error, dev sdb, sector 827392
[  351.712000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  352.268000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  352.824000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  353.380000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  353.936000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  354.492000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  354.648000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  354.648000] end_request: I/O error, dev sdb, sector 827632
[  355.048000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  355.600000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  356.156000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  356.712000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  357.268000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  357.824000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  357.980000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  357.980000] end_request: I/O error, dev sdb, sector 827872
[  358.380000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  358.936000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  359.492000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  360.048000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  360.604000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  361.160000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  361.316000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  361.316000] end_request: I/O error, dev sdb, sector 828112
[  361.716000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  362.272000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  362.828000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  363.384000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  363.940000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  364.552000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  364.708000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  364.708000] end_request: I/O error, dev sdb, sector 828352
[  365.108000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  365.660000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  366.216000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  366.768000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  367.324000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  367.880000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  368.036000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  368.036000] end_request: I/O error, dev sdb, sector 828592
[  368.532000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  369.064000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  369.596000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  370.128000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  370.660000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  371.192000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  371.348000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  371.348000] end_request: I/O error, dev sdb, sector 828928
[  371.748000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  372.304000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  372.860000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  373.416000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  373.972000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  374.528000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  374.684000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  374.684000] end_request: I/O error, dev sdb, sector 829168
[  375.084000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  375.640000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  376.196000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  376.752000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  377.308000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  377.864000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  378.020000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  378.020000] end_request: I/O error, dev sdb, sector 829408
[  378.420000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  378.972000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  379.528000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  380.084000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  380.636000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  381.188000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  381.344000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  381.344000] end_request: I/O error, dev sdb, sector 829648
[  381.884000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  382.440000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  382.996000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  383.548000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  384.104000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  384.656000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  384.812000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  384.812000] end_request: I/O error, dev sdb, sector 829984
[  385.188000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  385.720000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  386.252000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  386.788000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  387.320000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  387.852000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  388.008000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  388.008000] end_request: I/O error, dev sdb, sector 830224
[  388.384000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  388.920000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  389.452000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  389.988000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  390.524000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  391.056000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  391.212000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  391.212000] end_request: I/O error, dev sdb, sector 830464
[  391.612000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  392.164000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  392.716000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  393.272000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  393.824000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  394.376000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  394.532000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  394.532000] end_request: I/O error, dev sdb, sector 830704
[  395.072000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  395.624000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  396.180000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  396.736000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  397.292000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  397.848000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  398.004000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  398.004000] end_request: I/O error, dev sdb, sector 831040
[  398.400000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  398.952000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  399.504000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  400.056000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  400.608000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  401.160000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  401.316000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  401.316000] end_request: I/O error, dev sdb, sector 831280
[  401.716000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  402.272000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  402.828000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  403.384000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  403.936000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  404.492000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  404.648000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  404.648000] end_request: I/O error, dev sdb, sector 831520
[  405.024000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  405.556000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  406.088000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  406.620000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  407.156000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  407.688000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  407.844000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  407.844000] end_request: I/O error, dev sdb, sector 831760
[  408.364000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  408.920000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  409.476000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  410.028000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  410.584000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  411.136000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  411.292000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  411.292000] end_request: I/O error, dev sdb, sector 832096
[  411.688000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  412.240000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  412.792000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  413.344000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  413.896000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  414.448000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  414.604000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  414.604000] end_request: I/O error, dev sdb, sector 832336
[  415.004000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  415.560000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  416.112000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  416.664000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  417.220000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  417.776000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  417.932000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  417.932000] end_request: I/O error, dev sdb, sector 832576
[  418.328000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  418.880000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  419.432000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  419.984000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  420.536000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  421.088000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  421.244000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  421.244000] end_request: I/O error, dev sdb, sector 832816
[  421.764000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  422.320000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  422.876000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  423.432000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  423.988000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  424.544000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  424.700000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  424.700000] end_request: I/O error, dev sdb, sector 833152
[  425.096000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  425.648000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  426.200000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  426.752000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  427.304000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  427.856000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  428.012000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  428.012000] end_request: I/O error, dev sdb, sector 833392
[  428.408000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  428.960000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  429.512000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  430.068000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  430.624000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  431.180000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  431.336000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  431.336000] end_request: I/O error, dev sdb, sector 833632
[  431.732000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  432.284000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  432.836000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  433.388000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  433.940000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  434.492000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  434.648000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  434.648000] end_request: I/O error, dev sdb, sector 833872
[  435.168000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  435.720000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  436.276000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  436.828000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  437.380000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  437.932000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  438.088000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  438.088000] end_request: I/O error, dev sdb, sector 834208
[  438.484000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  439.036000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  439.588000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  440.144000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  440.696000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  441.248000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  441.404000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  441.404000] end_request: I/O error, dev sdb, sector 834448
[  441.800000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  442.356000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  442.908000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  443.460000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  443.892000] usb 3-1: USB disconnect, address 2
[  443.892000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  443.892000] end_request: I/O error, dev sdb, sector 834688
[  443.892000] Buffer I/O error on device sdb1, logical block 321
[  443.892000] lost page write due to I/O error on sdb1
[  443.892000] Buffer I/O error on device sdb1, logical block 324
[  443.892000] lost page write due to I/O error on sdb1
[  443.892000] Buffer I/O error on device sdb1, logical block 325
[  443.892000] lost page write due to I/O error on sdb1
[  443.892000] Buffer I/O error on device sdb1, logical block 326
[  443.892000] lost page write due to I/O error on sdb1
[  443.892000] Buffer I/O error on device sdb1, logical block 327
[  443.892000] lost page write due to I/O error on sdb1
[  443.892000] Buffer I/O error on device sdb1, logical block 328
[  443.892000] lost page write due to I/O error on sdb1
[  443.892000] Buffer I/O error on device sdb1, logical block 329
[  443.892000] lost page write due to I/O error on sdb1
[  443.892000] Buffer I/O error on device sdb1, logical block 577
[  443.892000] lost page write due to I/O error on sdb1
[  443.892000] Buffer I/O error on device sdb1, logical block 580
[  443.892000] lost page write due to I/O error on sdb1
[  443.892000] Buffer I/O error on device sdb1, logical block 581
[  443.892000] lost page write due to I/O error on sdb1
[  443.892000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  443.892000] end_request: I/O error, dev sdb, sector 834928
[  964.712000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[  964.884000] usb 3-1: configuration #1 chosen from 1 choice
[  964.888000] scsi3 : SCSI emulation for USB Mass Storage devices
[  964.888000] usb-storage: device found at 3
[  964.888000] usb-storage: waiting for device to settle before scanning
[  969.888000] usb-storage: device scan complete
[  969.980000] scsi 3:0:0:0: Direct-Access     BBK                       0100 PQ: 0 ANSI: 0 CCS
[  969.992000] sd 3:0:0:0: [sdb] 3005704 512-byte hardware sectors (1539 MB)
[  969.996000] sd 3:0:0:0: [sdb] Write Protect is off
[  969.996000] sd 3:0:0:0: [sdb] Mode Sense: 00 2a 00 00
[  969.996000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  970.008000] sd 3:0:0:0: [sdb] 3005704 512-byte hardware sectors (1539 MB)
[  970.012000] sd 3:0:0:0: [sdb] Write Protect is off
[  970.012000] sd 3:0:0:0: [sdb] Mode Sense: 00 2a 00 00
[  970.012000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  970.012000]  sdb: sdb1 sdb2
[  970.020000] sd 3:0:0:0: [sdb] Attached SCSI disk
[  970.020000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1148.672000] usb 3-1: USB disconnect, address 3
[ 1351.428000] UDF-fs: No VRS found
[ 1351.508000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1351.576000] ISOFS: changing to secondary root
[30326.316000] usb 3-1: new full speed USB device using uhci_hcd and address 4
[30326.488000] usb 3-1: configuration #1 chosen from 1 choice
[30326.492000] scsi4 : SCSI emulation for USB Mass Storage devices
[30326.492000] usb-storage: device found at 4
[30326.492000] usb-storage: waiting for device to settle before scanning
[30331.492000] usb-storage: device scan complete
[30331.584000] scsi 4:0:0:0: Direct-Access     BBK                       0100 PQ: 0 ANSI: 0 CCS
[30331.596000] sd 4:0:0:0: [sdb] 3005704 512-byte hardware sectors (1539 MB)
[30331.600000] sd 4:0:0:0: [sdb] Write Protect is off
[30331.600000] sd 4:0:0:0: [sdb] Mode Sense: 00 2a 00 00
[30331.600000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[30331.612000] sd 4:0:0:0: [sdb] 3005704 512-byte hardware sectors (1539 MB)
[30331.616000] sd 4:0:0:0: [sdb] Write Protect is off
[30331.616000] sd 4:0:0:0: [sdb] Mode Sense: 00 2a 00 00
[30331.616000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[30331.616000]  sdb: sdb1 sdb2
[30331.624000] sd 4:0:0:0: [sdb] Attached SCSI disk
[30331.624000] sd 4:0:0:0: Attached scsi generic sg2 type 0
cojones@tipping-point:~$ 

```

---

### Post by metalheart on 2007-12-05
Maybe the previous two files were still in process to be copied to the disk? Sometimes the File copy dialog closes, but the copying process is still running? Thats why you have to unmount disk, not just plug it off.

---

### Post by cisforcojo on 2007-12-05
Don't think that's it, I have tried unmounting. If no changes are made to the disk, it unmounts perfectly, if changes are made it seems to hang during unmounting/ejecting.

When unmounting I get no errors on the terminal btw.

---

