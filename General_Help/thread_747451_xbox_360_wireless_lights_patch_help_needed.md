---
title: "xbox 360 wireless lights patch help needed"
date: 2008-04-06
forum: General Help
---

### Post by bhuthogg on 2008-04-06
Wireless xbox 360 pad lights :(
can anyone tell me if there is a way to stop the lights flashing on the wireless pad once it is installed.

I'm pretty new to Linux and cutting and pasting code makes me a bit squeamish.

Sooooo. i was hoping someone could have a look over the following and kinda sling it together for me to test.

i have also found [http://lkml.org/lkml/2007/6/15/5](http://lkml.org/lkml/2007/6/15/5) which may or may not be any use?

Quote:
make
sudo rmmod xpad
sudo cp xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick
sudo depmod -a
sudo modprobe xpad
alongside this version (working but flashing light) of xpad360 attached


i have also found the following patch of which i am unsure if solves the problem and am unsure on how to insert it or where..



Quote:
--- a/xpad.c 2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c 2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
usb_set_intfdata(intf, xpad);

/* Turn off the LEDs on xpad 360 controllers */
- if (xpad->is360 && !xpad->isWireless) {
+ if (xpad->is360) {
char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
int j;
- usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+ struct usb_endpoint_descriptor *ep_irq_out;
+ ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+ usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
}

return 0;
so all in all its working in jscalibrator and working on games its just the circle of light on the controller is perm flashing

Hope someone can help me or its out with the insulating tape

---

