---
title: "usb727 verizon wireless air card packages?"
date: 2007-12-26
forum: General Help
---

### Post by eggl_link on 2007-12-26
On the back of the usb727 it says that its Linux compatible but,  there is no drivers on the CD or on there web page.  The lights on the usb device turn on like the device was found but in gnome nothing comes up telling me so. I was going to try ndiskwrapper but i cant fine a dll for this. i was wondering if anyone might have any ideas. Thanx

---

### Post by wormser on 2007-12-26
You will probably get faster help at [http://www.evdoforums.com](http://www.evdoforums.com).  Then post the solution here.

---

### Post by eggl_link on 2007-12-27
Thanks, Wormser. I will give that a try.

---

### Post by marcuscthomas on 2008-01-07
Verizon techs were not helpful in figuring this out.

Open the Terminal window and enter

                 sudo modprobe -r usbserial

enter your password if needed

then enter

                 sudo modprobe usbserial vendor=0x1410 product=0x4100

then enter 

                 sudo dmesg|grep -i ttyUSB

You should see the terminal reply that you have one or more attachments.  This last line is not needed, but it dumps the messages from the Kernel and lists those with the terms ttyUSB in them.  It is informative.

Your dialer should now see the USB device as ttyUSB0

if the dialer application does not see it, just manually create it.

gnome-ppp dialer detected the modem automatically, but KPPP did not for me.

If you edit the file: /etc/init.d/rc.local to add first two lines above (or all three), then the modem driver will automatically load on every restart.

to do this:

In Terminal type

                     sudo gedit /etc/init.d/rc.local

enter password if needed

edit the file that opens by placing (anywhere)

sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x1410 product=0x4100



[B]NOTE: For the U720, the second line (here and above) should be:

sudo modprobe usbserial vendor=0x1410 product=0x2110

The below list shows the vendor # followed by product # for several modems USB and PCCard and ExpressCard[/B]

I also have a PC5740 pc card EVDO modem and it is autodetected by gnome-ppp no problems.



Good luck!


NovatelMerlin S620 PCCARD
0x1410
0x1110

NovatelMerlin S720 PCCARD
0x1410
0x1130

NovatelOvation U720 USB MODEM
0x1410
0x2110

NovatelMerlin EX720 ExpressCard
0x1410
0x1120

NovatelU727 USB Modem
0x1410
0x4100

PantechPX-500  PCCard
0x106c
0x3702

Sierra AC580 PCCard
0x1199
0x0112

Sierra AC595 PCCard
0x1199
0x0019

Sierra AC595U USB Modem
0x1199
0x120

Sierra AC597E ExpressCard
0x1199
0x0021

---

