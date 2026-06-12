---
title: "Can't log into Google account using Chromium with USB authentication key"
date: 2022-03-17
forum: General Help
---

### Post by ReFranz on 2022-03-17
My desktop CPU is an AMD 64 x2 (512 k).  The machine is partitioned between Windows 10 and 20.04 LTS. I use Windows only for scanning documents and printing.  I use Chromium and Firefox, usually open at the same time. Logging into Google Accounts,I use a USB second-factor authentication key. Today when I attempted to open my Google account using Chromium, the key didn't flash. It still flashes and functions properly in Firefox--i opened my account using it. I visited the Bug Report page and followed the instructions for the heading "Collecting Information about a program with a window open." The result was a medium sized message window with "The crashed program seems to use third-party or local libraries," at the stop and many lines of script below it--unintelligible to me, as someone who is largely tech-illiterate. The "Send Problem Report" message window never appeared. 

I can't remember when I last logged into my Google account using Chromium--I got into the habit of using Firefox for the Google account after I couldn't use Chromium for Google Voice. That problem was solved, and I have used  Google Voice with Chromium on occasion--before this problem occurred.

---

### Post by TheFu on 2022-03-17
Which 2FA key, exactly, is being used?  They aren't all the same.  
My Yubikey 5C is different from my YubiKey 4 and NEO devices.
[https://www.yubico.com/products/identifying-your-yubikey/](https://www.yubico.com/products/identifying-your-yubikey/) has images of all Yubikeys produced.

Is there anything in the system log files about the device?

---

### Post by ReFranz on 2022-03-17
Thetis, FIDO2

---

### Post by QIII on 2022-03-17
Not a DE question.

Moved to General Help.

---

### Post by TheFu on 2022-03-17
> **ReFranz said:**
> Thetis, FIDO2

To my knowledge, FIDO2 is a protocol, not a device.  What device, exactly?

---

### Post by ReFranz on 2022-03-18
[https://thetis.io/products/thetis-fido2-security-key](https://thetis.io/products/thetis-fido2-security-key)

---

### Post by ReFranz on 2022-03-18
Solved. Sort of. My 2FA key is plugged into a multi-port USB hub that sits on my desk--and is connected to a direct port of the desktop.  It's also used for the USB keys for my wire-free keyboard and mouse. Also used to download photos from digital camera. NOT used with any connected appliances--i.e. no heavy loads. TheFu's questions about the sFA key eventually led me to place it in a direct-from-machine USB port--and the key worked with Chromium. Hopefully, this doesn't occur with Firefox, and I can leave the 2FA key in its accustomed convenient location. Thanks for helpful suggestion.

---

### Post by ActionParsnip on 2022-03-18
Are you going to unplug and replug in the USB key a lot?

---

### Post by TheFu on 2022-03-18
> **ReFranz said:**
> Solved. Sort of. My 2FA key is plugged into a multi-port USB hub that sits on my desk--and is connected to a direct port of the desktop.  It's also used for the USB keys for my wire-free keyboard and mouse. Also used to download photos from digital camera. NOT used with any connected appliances--i.e. no heavy loads. TheFu's questions about the sFA key eventually led me to place it in a direct-from-machine USB port--and the key worked with Chromium. Hopefully, this doesn't occur with Firefox, and I can leave the 2FA key in its accustomed convenient location. Thanks for helpful suggestion.

I always directly plug in my 2FA devices to a USB port on the computers.  More about not wasting a USB3 port for a HID than anything else. Some devices just don't work going through hub-->hub--> device connections. Most USB ports in computers are actually a hub. **lsusb -t** will show that.

I don't leave 2FA devices connected. Unsure if that matters for some types of security, but it could for others. Call me paranoid.  50% of security is user-behavior.  The extra effort of having a security device cannot negate misuse.
Not all of the supported protocols on my devices require anything more than just being present on to computer.  However, for FIDO and FIDO2, I think a touch is required.  Yubikeys have multiple modes which can be accessed by different touch lengths and different specific software.  A long touch does something different than a quick tap, for example.  I make use of 3 modes.

---

