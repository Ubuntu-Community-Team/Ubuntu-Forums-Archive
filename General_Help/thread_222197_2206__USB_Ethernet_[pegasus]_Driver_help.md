---
title: "2206  USB Ethernet [pegasus] Driver help"
date: 2006-07-24
forum: General Help
---

### Post by shawnrgr on 2006-07-24
I've read that this works for linksys usb modems. Where do I download this driver? and how do i install it? Im trying to get it working on and old box i have with debian sarge & blackbox installed... My modem is actually an ethernet modem with optional usb. please help, im desperate to get this old box online.

---

### Post by shawnrgr on 2006-07-24
anyone have any ideas? I know that the modem is visible because at boot up when i try and watch the usb stuff, i can see a few spots that say "Linksys USB Modem....." 

I also just saw the pegasus drive get loaded however after the pegasus driver loaded, other usb modem (i think) drivers loaded. would they over write the pegasus?

I have a cable connection not DSL. when i run ppoeconfig it detects a modem, says it found "eth0" but times out when trying to communicate.

is that for dsl only?

---

### Post by shawnrgr on 2006-07-25
after some more research i found this on linxquestions.org....

> The USB connection uses these modules

CDCEther
af_packet modules.

Tested on SuSE 9.0 the USB Modem hotplugs and loads the required drivers. All that needs to be done is to configure the interface

ifcfg-usb-eth

BOOTPROTO='dhcp'
STARTMODE='hotplug'

The device will take the first available eth device as in eth0, eth1, etc.

how do i do this?

---

### Post by shawnrgr on 2006-08-07
well you guys were so helpful thanks. 

i eventually figured it out. if anyone is trying to get there usb modem working. try these steps:

1. make sure CDCEther is loaded at start. modprobe CDCEther 
2. shut down pc
3. shut down modem
4. make sure only usb is plugede into the modem.
5. turn modem on and let completely boot up
6. turn pc on
7. if nothing at boot up thats fine. log in
8. at prompt: dhclient eth0

worked for me with my linksys usb modem on an older p1 ;) hopefully this can help a few people out.

---

