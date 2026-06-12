---
title: "help fixing usb mouse"
date: 2017-09-03
forum: General Help
---

### Post by anon89 on 2017-09-03
Hi all,
I can't figure out how to fix this... I don't like using my laptops trackpad, so I have a usb mouse.
When installing ubuntu, the usb mouse worked with no problems, but after install it no longer works
If i unplug and replug it then it works for a second then it stops again, I'm guessing its a driver issue, but why would it work in the usb live environment but not after installing ubuntu to hdd?
Any help is appreciated, thanks

---

### Post by Autodave on 2017-09-03
Have you tried something as simple as using another USB port?

Do you have any other wireless peripherals hooked up that could be interfering?

---

### Post by anon89 on 2017-09-04
Other usb ports don't fix it, and other usb devices work but I don't have another usb mouse to test
I have found entering into a terminal and typing "sudo rmmod usbhid" then plugging it in works, but stops if I take it out and replug it inow
And that command needs entered on every boot

---

