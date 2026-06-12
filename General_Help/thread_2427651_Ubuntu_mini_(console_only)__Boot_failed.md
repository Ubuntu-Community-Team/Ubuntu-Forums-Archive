---
title: "Ubuntu mini (console only) | Boot failed"
date: 2019-09-24
forum: General Help
---

### Post by prince-korvin on 2019-09-24
Hello guys!

We are running server on Ubuntu mini 18.04 with only console access. One day server was rebooted and after that we get "Boot failure. Press any key to continue." error. Grub is not loading (tried to hold shift when rebooting). I have made boot-repair disc and run a report: [http://paste.ubuntu.com/p/YPfBjpMRfB/](http://paste.ubuntu.com/p/YPfBjpMRfB/)

I have a feeling that it might be hardware issue (HDD).

Could you please help?

Thank you!

---

### Post by CatKiller on 2019-09-24
That's a BIOS message, nothing to do with the OS. If it started spontaneously (ie, without changing your BIOS configuration) then hardware failure is the likely culprit. Hard drive controller is another potential failure point, but the drive itself is more likely.

---

### Post by prince-korvin on 2019-09-25
Thank you. Any software suggestions to restore the data? We had a few important scripts there. And the backup versions are a bit old.
At least we can try to restore something.

---

