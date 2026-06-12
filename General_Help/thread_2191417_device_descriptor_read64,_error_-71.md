---
title: "device descriptor read/64, error -71"
date: 2013-12-02
forum: General Help
---

### Post by wolf_3d on 2013-12-02
Hello,

Sunday before last the computer started to display error messages during bootup "usb 1-1: device descriptor read/64, error -71"

This means that my mouse will not work because it is the only usb device plugged into the machine.

After some research I found some other people with the same problem. I followed the instructions on this page ([http://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error](http://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error)) and turned off the machine and unplugged the usb mouse. After a couple of minutes I plugged everything in, started it up and the problem fixed itself.

On Saturday it just started throwing up the same error message but now even after unplugging everything and waiting for a couple of minutes the problem keeps coming back and I have to use the keyboard to navigate around because the mouse isn't working.

When I tried it yesterday it worked perfectly well all day long. This evening when I turned it on it is has started showing the error messages again. This time I went into the terminal and ran the dmesg command. Here's the output;

```
[    0.209653] usbcore: registered new interface driver usbfs
[    0.209671] usbcore: registered new interface driver hub
[    0.209703] usbcore: registered new device driver usb
[    2.434380] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.434478] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    2.444033] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    2.444206] hub 1-0:1.0: USB hub found
[    2.444309] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.444397] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    2.502150] hub 2-0:1.0: USB hub found
[    2.502243] uhci_hcd: USB Universal Host Controller Interface driver
[    2.502317] usbcore: registered new interface driver libusual
[    2.760024] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.964022] usb 1-1: device descriptor read/64, error -71
[    3.272033] usb 1-1: device descriptor read/64, error -71
[    3.488020] usb 1-1: new high-speed USB device number 3 using ehci_hcd
[    3.692018] usb 1-1: device descriptor read/64, error -71
[    4.000018] usb 1-1: device descriptor read/64, error -71
[    4.216039] usb 1-1: new high-speed USB device number 4 using ehci_hcd
[    4.680028] usb 1-1: device not accepting address 4, error -71
[    4.792023] usb 1-1: new high-speed USB device number 5 using ehci_hcd
[    5.256066] usb 1-1: device not accepting address 5, error -71
[    5.256104] hub 1-0:1.0: unable to enumerate USB device on port 1
[    5.404030] usb 1-2: new high-speed USB device number 6 using ehci_hcd
[    5.608034] usb 1-2: device descriptor read/64, error -71
[    5.916053] usb 1-2: device descriptor read/64, error -71
[    6.132022] usb 1-2: new high-speed USB device number 7 using ehci_hcd
[    6.336039] usb 1-2: device descriptor read/64, error -71
[    6.644038] usb 1-2: device descriptor read/64, error -71
[    6.860042] usb 1-2: new high-speed USB device number 8 using ehci_hcd
[    7.324020] usb 1-2: device not accepting address 8, error -71
[    7.436035] usb 1-2: new high-speed USB device number 9 using ehci_hcd
[    7.900026] usb 1-2: device not accepting address 9, error -71
[    7.900046] hub 1-0:1.0: unable to enumerate USB device on port 2
[    8.048021] usb 1-3: new high-speed USB device number 10 using ehci_hcd
[    8.252024] usb 1-3: device descriptor read/64, error -71
[    8.560024] usb 1-3: device descriptor read/64, error -71
[    8.776023] usb 1-3: new high-speed USB device number 11 using ehci_hcd
[    8.980031] usb 1-3: device descriptor read/64, error -71
[    9.288030] usb 1-3: device descriptor read/64, error -71
[    9.504025] usb 1-3: new high-speed USB device number 12 using ehci_hcd
[    9.968027] usb 1-3: device not accepting address 12, error -71
[   10.080023] usb 1-3: new high-speed USB device number 13 using ehci_hcd
[   10.544027] usb 1-3: device not accepting address 13, error -71
[   10.544066] hub 1-0:1.0: unable to enumerate USB device on port 3
[   10.692021] usb 1-4: new high-speed USB device number 14 using ehci_hcd
[   10.896029] usb 1-4: device descriptor read/64, error -71
[   11.204022] usb 1-4: device descriptor read/64, error -71
[   11.420020] usb 1-4: new high-speed USB device number 15 using ehci_hcd
[   11.624021] usb 1-4: device descriptor read/64, error -71
[   11.932023] usb 1-4: device descriptor read/64, error -71
[   12.148038] usb 1-4: new high-speed USB device number 16 using ehci_hcd
[   12.612028] usb 1-4: device not accepting address 16, error -71
[   12.724021] usb 1-4: new high-speed USB device number 17 using ehci_hcd
[   13.188025] usb 1-4: device not accepting address 17, error -71
[   13.188041] hub 1-0:1.0: unable to enumerate USB device on port 4
[   13.336025] usb 1-5: new high-speed USB device number 18 using ehci_hcd
[   13.540028] usb 1-5: device descriptor read/64, error -71
[   13.848027] usb 1-5: device descriptor read/64, error -71
[   14.064023] usb 1-5: new high-speed USB device number 19 using ehci_hcd
[   14.268021] usb 1-5: device descriptor read/64, error -71
[   14.576026] usb 1-5: device descriptor read/64, error -71
[   14.792020] usb 1-5: new high-speed USB device number 20 using ehci_hcd
[   15.256025] usb 1-5: device not accepting address 20, error -71
[   15.368022] usb 1-5: new high-speed USB device number 21 using ehci_hcd
[   15.832028] usb 1-5: device not accepting address 21, error -71
[   15.832041] hub 1-0:1.0: unable to enumerate USB device on port 5
[   15.980029] usb 1-7: new high-speed USB device number 22 using ehci_hcd
[   16.184024] usb 1-7: device descriptor read/64, error -71
[   16.492024] usb 1-7: device descriptor read/64, error -71
[   16.708019] usb 1-7: new high-speed USB device number 23 using ehci_hcd
[   16.912026] usb 1-7: device descriptor read/64, error -71
[   17.220019] usb 1-7: device descriptor read/64, error -71
[   17.436020] usb 1-7: new high-speed USB device number 24 using ehci_hcd
[   17.900024] usb 1-7: device not accepting address 24, error -71
[   18.012020] usb 1-7: new high-speed USB device number 25 using ehci_hcd
[   18.476037] usb 1-7: device not accepting address 25, error -71
[   18.476057] hub 1-0:1.0: unable to enumerate USB device on port 7
[   18.624053] usb 1-8: new high-speed USB device number 26 using ehci_hcd
[   18.828058] usb 1-8: device descriptor read/64, error -71
[   19.136036] usb 1-8: device descriptor read/64, error -71
[   19.352039] usb 1-8: new high-speed USB device number 27 using ehci_hcd
[   19.556041] usb 1-8: device descriptor read/64, error -71
[   19.864053] usb 1-8: device descriptor read/64, error -71
[   20.080050] usb 1-8: new high-speed USB device number 28 using ehci_hcd
[   20.544025] usb 1-8: device not accepting address 28, error -71
[   20.656042] usb 1-8: new high-speed USB device number 29 using ehci_hcd
[   21.120035] usb 1-8: device not accepting address 29, error -71
[   21.120111] hub 1-0:1.0: unable to enumerate USB device on port 8
[   61.396048] usb 1-1: new high-speed USB device number 30 using ehci_hcd
[   61.600038] usb 1-1: device descriptor read/64, error -71
[   61.908046] usb 1-1: device descriptor read/64, error -71
[   62.124036] usb 1-1: new high-speed USB device number 31 using ehci_hcd
[   62.328027] usb 1-1: device descriptor read/64, error -71
[   62.636022] usb 1-1: device descriptor read/64, error -71
[   62.852025] usb 1-1: new high-speed USB device number 32 using ehci_hcd
[   63.316024] usb 1-1: device not accepting address 32, error -71
[   63.428027] usb 1-1: new high-speed USB device number 33 using ehci_hcd
[   63.892022] usb 1-1: device not accepting address 33, error -71
[   63.892038] hub 1-0:1.0: unable to enumerate USB device on port 1
[   64.040020] usb 1-2: new high-speed USB device number 34 using ehci_hcd
[   64.244034] usb 1-2: device descriptor read/64, error -71
[   64.552025] usb 1-2: device descriptor read/64, error -71
[   64.768023] usb 1-2: new high-speed USB device number 35 using ehci_hcd
[   64.972026] usb 1-2: device descriptor read/64, error -71
[   65.280028] usb 1-2: device descriptor read/64, error -71
[   65.496026] usb 1-2: new high-speed USB device number 36 using ehci_hcd
[   65.960023] usb 1-2: device not accepting address 36, error -71
[   66.072038] usb 1-2: new high-speed USB device number 37 using ehci_hcd
[   66.536025] usb 1-2: device not accepting address 37, error -71
[   66.536043] hub 1-0:1.0: unable to enumerate USB device on port 2
[   66.684025] usb 1-3: new high-speed USB device number 38 using ehci_hcd
[   66.888025] usb 1-3: device descriptor read/64, error -71
[   67.196024] usb 1-3: device descriptor read/64, error -71
[   67.412024] usb 1-3: new high-speed USB device number 39 using ehci_hcd
[   67.616019] usb 1-3: device descriptor read/64, error -71
[   67.924020] usb 1-3: device descriptor read/64, error -71
[   68.140025] usb 1-3: new high-speed USB device number 40 using ehci_hcd
[   68.604022] usb 1-3: device not accepting address 40, error -71
[   68.716023] usb 1-3: new high-speed USB device number 41 using ehci_hcd
[   69.180024] usb 1-3: device not accepting address 41, error -71
[   69.180042] hub 1-0:1.0: unable to enumerate USB device on port 3
[   69.328019] usb 1-4: new high-speed USB device number 42 using ehci_hcd
[   69.532021] usb 1-4: device descriptor read/64, error -71
[   69.840024] usb 1-4: device descriptor read/64, error -71
[   70.056018] usb 1-4: new high-speed USB device number 43 using ehci_hcd
[   70.260019] usb 1-4: device descriptor read/64, error -71
[   70.568021] usb 1-4: device descriptor read/64, error -71
[   70.784023] usb 1-4: new high-speed USB device number 44 using ehci_hcd
[   71.248025] usb 1-4: device not accepting address 44, error -71
[   71.360026] usb 1-4: new high-speed USB device number 45 using ehci_hcd
[   71.824030] usb 1-4: device not accepting address 45, error -71
[   71.824048] hub 1-0:1.0: unable to enumerate USB device on port 4
[   71.972032] usb 1-5: new high-speed USB device number 46 using ehci_hcd
[   72.176039] usb 1-5: device descriptor read/64, error -71
[   72.484041] usb 1-5: device descriptor read/64, error -71
[   72.700027] usb 1-5: new high-speed USB device number 47 using ehci_hcd
[   72.904022] usb 1-5: device descriptor read/64, error -71
[   73.212026] usb 1-5: device descriptor read/64, error -71
[   73.428031] usb 1-5: new high-speed USB device number 48 using ehci_hcd
[   73.892023] usb 1-5: device not accepting address 48, error -71
[   74.004029] usb 1-5: new high-speed USB device number 49 using ehci_hcd
[   74.468020] usb 1-5: device not accepting address 49, error -71
[   74.468040] hub 1-0:1.0: unable to enumerate USB device on port 5
[   74.616031] usb 1-7: new high-speed USB device number 50 using ehci_hcd
[   74.820026] usb 1-7: device descriptor read/64, error -71
[   75.128039] usb 1-7: device descriptor read/64, error -71
[   75.344036] usb 1-7: new high-speed USB device number 51 using ehci_hcd
[   75.548025] usb 1-7: device descriptor read/64, error -71
[   75.856046] usb 1-7: device descriptor read/64, error -71
[   76.072042] usb 1-7: new high-speed USB device number 52 using ehci_hcd
[   76.536025] usb 1-7: device not accepting address 52, error -71
[   76.648033] usb 1-7: new high-speed USB device number 53 using ehci_hcd
[   77.112029] usb 1-7: device not accepting address 53, error -71
[   77.112050] hub 1-0:1.0: unable to enumerate USB device on port 7
[   77.260024] usb 1-8: new high-speed USB device number 54 using ehci_hcd
[   77.464038] usb 1-8: device descriptor read/64, error -71
[   77.772024] usb 1-8: device descriptor read/64, error -71
[   77.988041] usb 1-8: new high-speed USB device number 55 using ehci_hcd
[   78.192048] usb 1-8: device descriptor read/64, error -71
[   78.500023] usb 1-8: device descriptor read/64, error -71
[   78.716032] usb 1-8: new high-speed USB device number 56 using ehci_hcd
[   79.180030] usb 1-8: device not accepting address 56, error -71
[   79.292035] usb 1-8: new high-speed USB device number 57 using ehci_hcd
[   79.756028] usb 1-8: device not accepting address 57, error -71
[   79.756047] hub 1-0:1.0: unable to enumerate USB device on port 8

```

When I run lsusb the mouse isn't showing. It is a Logitech mouse and ASUS motherboard. I have a full dmesg log but I'm reluctant to post it because there appears to be IP addresses in it.

I have already tried a different usb mouse with the same result. And I used a PS2-to-USB converter and it still complained about the above error message.

Can anyone help?

---

### Post by Keith_Beef on 2013-12-03
I have a similar problem with a device, I posted about it [here]("http://ubuntuforums.org/showthread.php?t=2191520").

I suggest we keep an eye on each other's threads to see if there is a common cause and solution to the problem we both have.

---

### Post by wolf_3d on 2013-12-03
I thought it might be a problem with the kernel.

I was running the 3.2.0-56 (Ubuntu 12.04) kernel so I tried loading some of the older ones to see if the problem still exists. I tried 3.2.0-49 and the oldest kernel I have is 3.2.0-23 but the problem is still there on all of them.

Today the 3.2.0-57 kernel is in the updates so I have installed it but it won't appear in my grub list for some reason. I've tried updating grub with update-grub and I saw the 3.2.0-57 in the list but it doesn't appear when I restart the computer.

---

### Post by Keith_Beef on 2013-12-04
I just updated my [other thread]("http://ubuntuforums.org/showthread.php?t=2191520") with some more info; but no solution, yet.

---

### Post by wolf_3d on 2013-12-05
Last night it worked fine all night long.

Turned it on this evening and its back to displaying the error message again.

---

### Post by wolf_3d on 2013-12-08
Bump - please.

---

