---
title: "System fails to detect USB device - Blackberry"
date: 2008-03-24
forum: General Help
---

### Post by Patb on 2008-03-24
Hi. The helpful folk at Blackberry forums suggested I look for a solution here.  When I plug my Blackberry directly into a USB port, Ubuntu fails to detect it.  Unless I can get my Linux box to detect the device, I will not be able to synchronise the address book etc using the tools in the Barry project (which syncs a Blackberry under Linux).

Some possibly relevant output (with the device connected) follows:
```
pat@ubuntu:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
```
(There is nothing interesting from "lsusb -v" either.)

```
pat@ubuntu:~$ lsmod | grep -i usb
usbhid                 29536  0 
hid                    28928  1 usbhid
usbcore               138632  5 uhci_hcd,usbhid,ehci_hcd,ohci_hcd
```

```
pat@ubuntu:~$ dmesg | tail
[  192.056341] usb 2-1: USB disconnect, address 25
[  192.065127] usb 2-1: usbfs: USBDEVFS_CONTROL failed cmd bcharge rqt 64 rq 162 len 0 ret -108
[  192.729991] usb 2-1: new full speed USB device using ohci_hcd and address 26
[  192.942381] usb 2-1: configuration #1 chosen from 1 choice
[  193.293189] usb 2-1: USB disconnect, address 26
[  193.309213] usb 2-1: usbfs: USBDEVFS_CONTROL failed cmd bcharge rqt 64 rq 162 len 0 ret -108
[  193.969411] usb 2-1: new full speed USB device using ohci_hcd and address 27
[  194.182245] usb 2-1: configuration #1 chosen from 1 choice
[  194.764894] usb 2-1: USB disconnect, address 27
[  194.799812] usb 2-1: usbfs: USBDEVFS_CONTROL failed cmd bcharge rqt 64 rq 162 len 0 ret -108
```

For what it's worth, the "bcharge" command in the output from dmesg is one of the tools within the Barry project. But I have not actually issued the command in this session, so I'm surprised it is there.  

How can I get Ubuntu to recognise the device?  Any suggestions would be much appreciated.  

Cheers, Pat.

---

### Post by Patb on 2008-03-24
Bump.  Can anyone suggest where I might start to investigate why my system happily detects lots of usb devices (mouse, printer, camera, usb stick, pda etc) but inexplicably fails to detect a blackberry of just a few years vintage?  Any pointers appreciated.  

Cheers, Pat

---

### Post by Bluebell392 on 2008-03-25
Do you have the correct software installed for it?

---

### Post by Patb on 2008-03-25
Thanks, Bluebell.  Yes, I have the correct package "Barry" installed.  But if my system doesn't first recognise the device, there is no possible way Barry will be able to communicate with it.  

I am not sure what I have to do to find out why my Linux box will not recognise the device.  I don't know where to start looking apart from the commands for which I have already listed output.  

I would be grateful for any further suggestions/ideas.

Cheers, Pat.

---

### Post by Patb on 2008-04-01
It seems perhaps this is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/152742/+viewstatus").  

I have not been able to make a workaround.   

Cheers, Pat

---

### Post by karlatsaic on 2008-05-07
I just upgraded to Hardy 8.04

I just discovered on my first trip with my blackberry that it wouldn't charge off the usb port automatically. After a search of this forum I just downloaded the barry utilities from [http://sourceforge.net/projects/barry/](http://sourceforge.net/projects/barry/) in order to solve the problem as well as providing backup and sync utilities. I grabbed barry-util, libbarry, barrybackup-gui, libopensyc-plugin-barry, all at 0.12-1, with the ubuntu7.10.deb suffix (as there is none for 8.04). I also made sure my configuration had all the recommended debian packages prior to doing the manual install of the 4 barry packages. After rebooting, typing *bcharge* at the command line detected my blackberry 8800, so now I can go to sleep in my hotel room, with a fully charged blackberry in the a.m. :-)

[edit]Just to be clear, the extra packages I had to add via synaptic were: libusb-dev, libssl-dev, libtar-dev, libgtkmm-2.4-dev, libglademm-2.4-dev, zlib1g-dev

---

### Post by halw on 2008-05-12
karlatsaic,

Have you been able to sync your Blackberry to Evolution yet?

I have a Palm Treo 755p right now but am considering the BB 8830 from Verizon. I have about 7 days left on the 14 day trial with the palm and am trying to decide whether to keep it or return for Blackberry.

---

### Post by karlatsaic on 2008-05-12
I don't do that directly. My primary purpose with going with a corporate blackberry is its incredible integration with exchange server (which is one of those Microsoft things which works well in my opinion). So our corporate MS Exchange server is the central hub for keeping work and home desktops and laptops, as well as my blackberry all in sync, with ALL my >10 GB of mail going back 20 yrs on a linux imap server). It turns out that integrates more nicely with Evolution at our site than Outlook (go figure). So my blackberry is integrated instantaneously (1-3 secs, really) with Evolution with MS Exchange in the middle. I'm sure that's not the answer you were hoping for :-) As Mr. Natural says, "use the right tool for the job"

---

