---
title: "How to detect my mobile device when connected to USB??"
date: 2008-03-27
forum: General Help
---

### Post by krprabhakar2003 on 2008-03-27
Plzz help me out from this, I am using nokia 3500 and when connected to system via usb im not able to detect my mobile device. Do I need any software for this to detect my moble device??

---

### Post by Zimmer on 2008-03-27
In my experience you are unlikely to detect the 'phone' and normally require Nokia software (Windows) to access the phone directly using USB.

If you have an additional memory card installed in it then there may be an option in the phone settings to allow the USB to connect as MASS STORAGE DEVICE.

This will allow you to plug the phone into the PC and the additional storage should be recognised and mounted the same as a USB memory stick.

This is how my SAMSUNG U600 deals with it. So if you save your photos music etc. to the additional storage you have access to the files easily .

As for the phone itself, Calendar addresses etc. there may be ways to access it but if you have the nokia software already for Windows why not try installing that using WINE.

Tried Bluetooth a few times with my last Motorola, but it was less than satisfactory and I found it easier to remove the SD card and put it in a card reader.

PS
[http://ubuntuforums.org/showthread.php?t=720592&highlight=Nokia](http://ubuntuforums.org/showthread.php?t=720592&highlight=Nokia)
Someone seems to have had some success with Bluetooth...
Good luck

---

### Post by rfs1970 on 2008-04-06
Hi Zimmer

I have the very same mobile than you (samsung u600), but there is no way to connect it via ubuntu.

I did try all the 3 options once I connect the usb cable, but none works.
Can you give me any tip?

Thank you,

---

### Post by Zimmer on 2008-04-07
It works if you have a micro SD card installed as additional storage (as explained above)

From Menu:
Option 12-Settings
Option 2 -Phone
Option 9 -USB Settings

select last option  MASS STORAGE
Then...
Connect phone with USB cable.
 (Does not work changing the option with cable connected).

Device should appear in  Places>Computer   so you may need to right click and mount the device (unless already mounted if you have the option to do that set in your Preferences)

---

### Post by rfs1970 on 2008-04-18
Hi Zimmer,

Yes, I do have a micro SD inserted in my samsung,
but after I did what you said, I got this log from my dmesg:

[ 2178.848000] usb 5-8: new high speed USB device using ehci_hcd and address 8
[ 2178.980000] usb 5-8: configuration #1 chosen from 1 choice
[ 2178.980000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 2178.980000] usb-storage: device found at 8
[ 2178.980000] usb-storage: waiting for device to settle before scanning
[ 2183.980000] usb-storage: device scan complete
[ 2183.980000] scsi 5:0:0:0: Direct-Access     SAMSUNG  ECLAIR USB MASS  1.00 PQ: 0 ANSI: 2
[ 2183.980000] sd 5:0:0:0: [sdf] 494080 512-byte hardware sectors (253 MB)
[ 2183.984000] sd 5:0:0:0: [sdf] Write Protect is off
[ 2183.984000] sd 5:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 2183.984000] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[ 2183.984000] sd 5:0:0:0: [sdf] 494080 512-byte hardware sectors (253 MB)
[ 2183.984000] sd 5:0:0:0: [sdf] Write Protect is off
[ 2183.984000] sd 5:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 2183.984000] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[ 2183.984000]  sdf: sdf1
[ 2184.020000] sd 5:0:0:0: [sdf] Attached SCSI removable disk
[ 2184.020000] sd 5:0:0:0: Attached scsi generic sg5 type 0


But there is no way to mount it...
My system doesnt recognize the device sdf1

:(

---

### Post by Zimmer on 2008-04-20
pr 21 02:11:10 localhost kernel: [17183165.024000] usb 4-1: new high speed USB device using ehci_hcd and address 4
Apr 21 02:11:11 localhost kernel: [17183165.264000] Initializing USB Mass Storage driver...
Apr 21 02:11:11 localhost kernel: [17183165.264000] scsi0 : SCSI emulation for USB Mass Storage devices
Apr 21 02:11:11 localhost kernel: [17183165.264000] usbcore: registered new driver usb-storage
Apr 21 02:11:11 localhost kernel: [17183165.264000] USB Mass Storage support registered.
Apr 21 02:11:16 localhost kernel: [17183170.264000]   Vendor: SAMSUNG   Model: ECLAIR USB MASS   Rev: 1.00
Apr 21 02:11:16 localhost kernel: [17183170.264000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Apr 21 02:11:16 localhost kernel: [17183170.300000] Driver 'sd' needs updating - please use bus_type methods
Apr 21 02:11:16 localhost kernel: [17183170.300000] SCSI device sda: 990976 512-byte hdwr sectors (507 MB)
Apr 21 02:11:16 localhost kernel: [17183170.304000] sda: Write Protect is off
Apr 21 02:11:16 localhost kernel: [17183170.352000] SCSI device sda: 990976 512-byte hdwr sectors (507 MB)
Apr 21 02:11:16 localhost kernel: [17183170.352000] sda: Write Protect is off
Apr 21 02:11:16 localhost kernel: [17183170.352000]  sda: sda1
Apr 21 02:11:16 localhost kernel: [17183170.380000] sd 0:0:0:0: Attached scsi removable disk sda
Apr 21 02:11:16 localhost kernel: [17183170.392000] sd 0:0:0:0: Attached scsi generic sg0 type 0

is the output from my log
It also appears in the 'Disks' option in System>Administration   

I m using Dapper 6.06 on a 32 bit install 

What have you got set in Preferences>Removeable drives and media? 
Otherwise I am at a loss to accurately  say what  the problem is.
 
One guess is that the 7.10 version of Ubuntu uses a different  method of naming drives to assist/cope with SATA interfaces . 

Can you not mount it from the terminal addressing it as sdf1?  

Anyone else out there got any suggestions... it is late here and I must sleep, I will try and investigate yor log a bit more in the morning...

---

### Post by ryanhaigh on 2008-04-20
I have used gammu myself for my sony ericsson phone but others available might be better for the nokia:
[wammu](apt://wammu)
[gammu](apt://gammu)
[gnokii](apt://gnokii)
[gnome-phone-manager](apt://gnome-phone-manager)
[kmobiletools](apt://kmobiletools)
Just click the links to install.

---

### Post by Zimmer on 2008-04-26
rfs1970  

Have you solved the problem yet?   Have you formatted the card..
or is there a conflict in fstab with a card reader you may have on your machine?

as witnessed  in this link?
[http://www.suseforums.net/index.php?showtopic=42697](http://www.suseforums.net/index.php?showtopic=42697)

Regards
Zimmer

---

### Post by rfs1970 on 2008-05-06
Hi Zimmer,

Unhappily I couldn't solve the problem till now...
I can't access the card, so how can I format it?

:(

---

### Post by Zimmer on 2008-05-07
Have you saved anything important to the card on the phone so far?
If not, try formatting the card with the Phone. 
Menu> Myfiles>Memory card>Options>Memory card settings>Format Card.

Do you have the SD adapter for the card and a card reader for your PC?

Pop the little card in the adapter and the adapter in the card reader. 
The card reader should mount and show the file system on the card.

This is how I accessed this type of card when I had a Motorola but no proprietary USB lead for a Motorola phone. I just popped the card in an adapter and the adapter in the reader.

As the Samsung comes with a USB cable I can cut out the card reader...

Try a card reader, see if the card is at fault.

EDIT: managed to use Bluetooth the other day messing with Mepis and MCNLive distributions.
Managed to connect and send direct to the phone file system...

---

