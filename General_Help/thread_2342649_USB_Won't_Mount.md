---
title: "USB Won't Mount"
date: 2016-11-08
forum: General Help
---

### Post by eldavar on 2016-11-08
Good afternoon. 

I've got a USB stick that won't mount. When I look for it with **[FONT=courier new]sudo fdisk -l [/FONT]**it doesn't show up. It also doesn't appear in Gparted. 

It **does** appear in the Drive utility, but there's no information. 

[IMG]https://lh3.googleusercontent.com/0D5fSy1-OeHvTMWC7alkWbHwcGuesD9L6wI1TahF5HruFB1v0sPqirVYOa-dt7B0T8UMw36Mwf3BebZ9BU-7EpZmrSQgIGa3ZPupFx1FeN-h7DeTdQrllIJvOMvzM-qkkEBNCsXXgRgFI1Z7ocMSXtjNveIriRFY5s64ZBkf05pQy1w6XL-reyfeDnPyl_jcHePQHJOMNjM2POfiuh6q90DGuEoKyk-8Sj5sze17BmE3BdxrxMuNKZI4TotOD3TlWdyyGnp7rtHz1x9u4QY9l3E4UjpYxfQlR-ANvWbQIhgXebpL8VBoHN3gvLmrUU2HTZ94DQ0kGHv2w87lTxEC8aAscZsBPrld_W7S__aU-dV3bwOE3ynFz5KVRcjaI9Hjw6YiC3JQoEDfk1zmJ6jQV1NrEOvsbwvy-V8bEeA3Rs7X_Ukk6OTZBph7N2z5jZlp519U8dWGH8OMkbgFZXFzZ8u1hyqw0UOp8MQ7zeEMVqVL-bhuRCTT_lL2py5fltRm8M7_Y1MCOSptCuKzh10AQRWz8-m-8LirvQObV9dqA94S196gasJUN7-iXpThCUTsWRyWbyyg-rfaJ19NXVB7CDM2tPt_76owutYdzq6IeZnvfaXDBQ=w797-h468-no[/IMG]

I've tried turning the automatic mount options off, checking the boxes for mount at startup and show in user interface, typing the mount point, but still it doesn't show up. I looked with dmesg and it shows that USB stick is recognized. 

```
[268146.773057] usb 10-2.3.3: new high-speed USB device number 24 using xhci_hcd
[268146.862605] usb 10-2.3.3: New USB device found, idVendor=058f, idProduct=1234
[268146.862609] usb 10-2.3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[268146.862611] usb 10-2.3.3: Product: Mass Storage Device
[268146.862612] usb 10-2.3.3: Manufacturer: Alcor Micro
[268146.864075] usb-storage 10-2.3.3:1.0: USB Mass Storage device detected
[268146.864239] scsi host21: usb-storage 10-2.3.3:1.0
[268147.861741] scsi 21:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 4
[268147.862076] sd 21:0:0:0: Attached scsi generic sg2 type 0
[268147.863104] sd 21:0:0:0: [sdc] Attached SCSI removable disk

```
So, I'm at a loss now for what to do. Any ideas or insights would be greatly appreciated. Thanks!

---

