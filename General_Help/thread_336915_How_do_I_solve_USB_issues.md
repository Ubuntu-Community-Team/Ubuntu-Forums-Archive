---
title: "How do I solve USB issues?"
date: 2007-01-12
forum: General Help
---

### Post by wersdaluv on 2007-01-12
I was thinking if there is a driver for my laptop's usb slot so I went to BenQ's support website to look for one, but I didn't find what I was looking for.

I'm just wondering why I'm having problems with any USB device that I connect to my laptop. I'm wondering if it's just because my stuff are not supported by Ubuntu or I just need to tweak something. 

What doesn't work? My webcams, my printers, my usb mouse (which works when it's plug since my laptop is booted but when it works, the mouse pointer moves very slowly), my network walkman, and my USB card reader. As for my printer/scanner, I have installed SANE but it can't detect the device; as for my other printer, Ubuntu has a driver for it but it still can't detect it; as for my USB mouse, I don't know what's going on. 

It's so weird. I don't think this OS is that hard to find support with (is it?).

What can I tweak to make things work?

---

### Post by netadptr0719 on 2007-01-12
What laptop model is it?

---

### Post by wersdaluv on 2007-01-13
It's a BenQ Joybook R31E

---

### Post by foxmulder881 on 2007-01-13
The fact you stated that you're card reader doesn't work is a dead giveaway that your USB ports may require some Linux drivers as card reader generally work with any OS being Windows/Linux/Mac. They're just plug in and play. Contact BenQ and see what they have to say.

---

### Post by wersdaluv on 2007-01-13
Thanks. I'll do that, but before everything else, should I really be expecting a reaction from my laptop whenever I plug the USB Card reader and should I be looking for the card reader on the root/media folder?

---

### Post by tribaal on 2007-01-13
Could you please post the output of "lsusb" before and after you plug in your non-working peripheral please?
Maybe it'll give us a clue ;)

- trib'

---

### Post by wersdaluv on 2007-01-13
lsusb without the USB card reader:

```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```





lsusb with the USB card reader plugged:

```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```
That's what comes out but it comes out very slowly at first when the device is just plugged

---

### Post by foxmulder881 on 2007-01-13
> **wersdaluv said:**
> Thanks. I'll do that, but before everything else, should I really be expecting a reaction from my laptop whenever I plug the USB Card reader and should I be looking for the card reader on the root/media folder?

When you click on Places menu and go into Computer, each memory slot should be displayed.

---

### Post by wersdaluv on 2007-01-13
> **foxmulder881 said:**
> When you click on Places menu and go into Computer, each memory slot should be displayed.

I'm using Kubuntu Edgy. Where can I find it?

---

### Post by foxmulder881 on 2007-01-14
> **wersdaluv said:**
> I'm using Kubuntu Edgy. Where can I find it?

Sorry, I just assumed you were working with Ubuntu Gnome desktop. Didn't realize you were using KDE.

I haven't used the KDE for quite sometime, therefore I honestly can't remember. There must be an option to go into Computer (a Windows My Computer equivalent). Check around.

---

