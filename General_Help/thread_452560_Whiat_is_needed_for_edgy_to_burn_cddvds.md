---
title: "Whiat is needed for edgy to burn cd/dvds??"
date: 2007-05-23
forum: General Help
---

### Post by 999alfred on 2007-05-23
I have always used Slackware before Unbuntu and enabled scsi emulation to be able to use xcdroast/cdrecord. I have read some previous posts and their seems to be some contention about what is needed to use cdrecord.

So, can someone please explain what is needed to burn cd/dvds under Ubuntu Edgy?

tj

---

### Post by DoktorSeven on 2007-05-23
SCSI emulation in the kernel is no longer required.  CD burning should work by default.

cdrecord dev=/dev/yourcdromdevice cdimage.iso should work just fine.

---

### Post by munkyeetr on 2007-05-23
I installed gnomebaker from the repositories and it works fine for me.

---

