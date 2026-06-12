---
title: "How do I give my account permission to use my Camera?"
date: 2007-01-02
forum: General Help
---

### Post by badgaz1 on 2007-01-02
When I try and import photos from my Digital camera (Kodak P850) using my normal account it says:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.


But when I try using root it works flawlessly, how can I fix this?

Thanks.

---

### Post by GeirG on 2007-01-02
Hi,
 This helped me: 
[https://launchpad.net/distros/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/distros/ubuntu/+source/libgphoto2/+bug/64146)

---

### Post by ~LoKe on 2007-01-02
Link is slightly messed up.  Here's the fix.
**EDIT:** Ah, you fixed it.

---

### Post by badgaz1 on 2007-01-02
Wahey I managed to use that to fix it thanks a lot! :KS

---

### Post by GeirG on 2007-01-03
Your very welcome :-)

---

