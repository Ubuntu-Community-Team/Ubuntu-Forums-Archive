---
title: "system program problem detected"
date: 2019-07-11
forum: General Help
---

### Post by bobptz on 2019-07-11
Hi

I have Ubuntu 18.04 on my desktop (I5, 8 GB ram).  Whenever I start the pc, after 2-3 minutes I see the following error message:  **system program problem detected**

I click on "Report Problem", but nothing happens, the message just goes away.

I checked the disks and they seem ok. 

Here is the result of dmesg :
[https://paste.ubuntu.com/p/9bmGJyPwDD/](https://paste.ubuntu.com/p/9bmGJyPwDD/)

---

### Post by kpatz on 2019-07-11
Clear the crash reports folder with **sudo rm /var/crash/*** and the error should go away.

If it comes back again something new crashed and probably should be investigated further.

---

### Post by bobptz on 2019-07-11
It worked!  Thank you so much.

---

### Post by Dennis N on 2019-07-11
Set Error Reporting preferences in Settings > Privacy.
See attached Screenshot.

You can turn reports off, or opt to send them automatically without the notification popup.

---

### Post by bobptz on 2019-07-11
> **Dennis N said:**
> Set Error Reporting preferences in Settings > Privacy.
See attached Screenshot.

You can turn reports off, or opt to send them automatically without the notification popup.
I prefer to know when something is wrong.

---

