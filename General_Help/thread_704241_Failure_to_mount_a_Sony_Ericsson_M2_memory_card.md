---
title: "Failure to mount a Sony Ericsson M2 memory card"
date: 2008-02-22
forum: General Help
---

### Post by WhoDaBear on 2008-02-22
Hi folks,

Here's my problem (using 6.06LTS);

Yesterday, on plugging my Sony Ericcson phone in via USB, it automounted the M2 media in it, and asked me if I wanted to import photos etc.  All good.  I happily transfered files to my hearts content.

Today, it doesn't.  Plugging it into a variety of USB ports provides no joy.  I read a few similar posts and thought I'd try:

[PHP]dmesg | tail[/PHP]

Which gives rise to:
[17180913.380000] usb 2-1: new full speed USB device using uhci_hcd and address 23
[17180913.500000] usb 2-1: device descriptor read/64, error -71
[17180913.724000] usb 2-1: device descriptor read/64, error -71
[17180913.940000] usb 2-1: new full speed USB device using uhci_hcd and address 24
[17180914.060000] usb 2-1: device descriptor read/64, error -71
[17180914.284000] usb 2-1: device descriptor read/64, error -71
[17180914.500000] usb 2-1: new full speed USB device using uhci_hcd and address 25
[17180914.908000] usb 2-1: device not accepting address 25, error -71
[17180915.020000] usb 2-1: new full speed USB device using uhci_hcd and address 26
[17180915.428000] usb 2-1: device not accepting address 26, error -71

I though I'd also do:
[PHP]sudo fdisk -l[/PHP]

..which, to cut it short, acknowledges the existence of sda and sdb , my two hard-discs only.

My CD-ROM drive automounts just fine still (I just checked it).

I hereby throw myself at the mercy of the Ubuntu community, and thank y'all in advance.

p.s. I'm close to linux clueless (don't you just love threads that say that?)

---

### Post by WhoDaBear on 2008-02-24
Just bumping this.  Anyone have any ideas?
Thanks.

---

### Post by gustavolaufer on 2008-03-30
Have you gotten that answer?

Can you mount that now?

I am trying to mount that on a Notebook Gateway, using the memory stick duo adaptor and I have no success

let me show the dmesg
when i connect
[HTML][ 7995.132000] tifm_core: MemoryStick card detected in socket 0:0
[ 7995.140000] tifm_ms: Unknown symbol tifm_has_ms_pif[/HTML]

When I remove the card
[HTML][ 8082.064000] tifm0 : demand removing card from socket 0:0[/HTML]


but on fdisk -l there is no difference.

So, I believe that the system couldn't reach that memory card

ps1. MS Windows can reach that
ps2. Connecting the phone direct to the computer I have success, however that is not what I want, as soon as the phone is unplugged - disconnected from the network.


Can you give me any advice?

---

### Post by bapoumba on 2008-03-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159951](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159951) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **gustavolaufer said:**
> 
ps2. Connecting the phone direct to the computer I have success
This is what I do, with the usb cable, and it works too.
Maybe check the bug report.

---

