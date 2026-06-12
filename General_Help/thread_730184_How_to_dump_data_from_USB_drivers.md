---
title: "How to dump data from USB drivers?"
date: 2008-03-20
forum: General Help
---

### Post by swapnova on 2008-03-20
Hi guys, 

I'm trying to monitor the information passing through a usb port. How can I get into the drivers and dump the information to a file? Thanks in advance for your help.

---

### Post by ruy_lopez on 2008-03-20
This [article]("http://www.linuxjournal.com/article/7582") documents how to modify the kernel to send usbfs data to kernel.log.

---

### Post by swapnova on 2008-03-25
Thanks that aticle helped, but his approach was only able to monitor control information. I would actually like to create something of a file sink at the usb port so I can dump all of the actual data into passing through into it. Any ideas?

---

### Post by dcstar on 2008-03-25
> **swapnova said:**
> Thanks that aticle helped, but his approach was only able to monitor control information. I would actually like to create something of a file sink at the usb port so I can dump all of the actual data into passing through into it. Any ideas?

**man tee**

---

