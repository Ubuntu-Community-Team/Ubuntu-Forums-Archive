---
title: "removable hard drive problem.....not recognized!!  (stumped)"
date: 2007-06-21
forum: General Help
---

### Post by johnnyoc3 on 2007-06-21
i recently bought an acomdata 500gb usb2.0 external hard drive that works wonders with my dell inspiron e1405 in windows. however when i try to use it on the same machine in ubuntu it does nothing. i plug the device in turn it on and then start the computer. after it boots the device is not present and doesnt show up in a "sudo fdisk -l"  and i cant seem to find it in the usual places like /media/ and /dev/  . 

in addition i booted off of a gparted cd and it could not detect the hard drive. i think the problem stems from the fact that it has two partitions on the hard drive. in windows one shows as a cd drive and the rest is the hard drive. the cd is filled with bloatware and a small ability to disable/enable password protection which i have of course turned off. 

there is most likely just an internal hard drive inside of it but i cant figure out how to open it up :( 
 i've seen a couple of other posts regarding this problem with acomdata but none of them seem to have a definitive solution. other people HAVE said that they can get the hard drive working but know one has said how.


thanks a bunch,
john

---

### Post by AlexThomson_NZ on 2007-06-21
How is the drive connected?  USB, eSATA, firewire?

Does anything show in dmesg?

---

### Post by johnnyoc3 on 2007-06-22
its usb 2

and dmesg says

```

[  106.588000] usb 5-5: new high speed USB device using ehci_hcd and address 3
[  106.992000] usb 5-5: new high speed USB device using ehci_hcd and address 4
[  108.504000] usb 5-5: new high speed USB device using ehci_hcd and address 8
[  109.008000] usb 5-5: new high speed USB device using ehci_hcd and address 9
[  109.764000] usb 5-5: new high speed USB device using ehci_hcd and address 11
[  110.772000] usb 5-5: new high speed USB device using ehci_hcd and address 13
[  111.276000] usb 5-5: new high speed USB device using ehci_hcd and address 14
[  112.536000] usb 5-5: new high speed USB device using ehci_hcd and address 18
[  114.804000] usb 5-5: new high speed USB device using ehci_hcd and address 26
[  115.308000] usb 5-5: new high speed USB device using ehci_hcd and address 27
[  116.064000] usb 5-5: new high speed USB device using ehci_hcd and address 28
[  116.936000] hub 5-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[  117.324000] usb 5-5: new high speed USB device using ehci_hcd and address 30
[  118.080000] usb 5-5: new high speed USB device using ehci_hcd and address 31
[  119.088000] usb 5-5: new high speed USB device using ehci_hcd and address 33
[  119.844000] usb 5-5: new high speed USB device using ehci_hcd and address 34
[  120.348000] usb 5-5: new high speed USB device using ehci_hcd and address 35
[  120.852000] usb 5-5: new high speed USB device using ehci_hcd and address 36
[  122.112000] usb 5-5: new high speed USB device using ehci_hcd and address 39
[  122.616000] usb 5-5: new high speed USB device using ehci_hcd and address 40


```

weird because i know the cable is good. i guess i can try a different one?
ive tried all the usb ports on my comp and i get the same error message just at a different port # like usb 5-6

---

### Post by AlexThomson_NZ on 2007-06-22
It won't be the cable if it works in Windows.  Would be interested to see if there is a conflict of some sort though- maybe try a different USB port?

---

### Post by johnnyoc3 on 2007-06-22
yeah i did. i guess i can try another one? also i have know other usb devices attached right now so i dont know if that means anything. i just tried another cable and no luck. :(

---

### Post by johnnyoc3 on 2007-06-22
should i try this?

[http://ubuntuforums.org/showpost.php?p=1925647&postcount=6](http://ubuntuforums.org/showpost.php?p=1925647&postcount=6)

i have no clue how to go about doing it though

---

### Post by taseedorf on 2008-01-09
I think the problem you're getting is in regards to a known bug which won't let Ubuntu mount a drive (usb) that has been improperly unmounted on windows.  Do you always use "safely remove hardware"??  Anyways, I believe you can fix it by setting it up on windows, hitting safely remove hardware, than turning the drive off if possible, and than unplugging.  Than try it in Ubuntu and it should work, let me know if it did.  Oh, btw, I think this is an issue that DOES need to be fixed with windows, ie, you can't simply try to type a command or workaround in linux.

---

