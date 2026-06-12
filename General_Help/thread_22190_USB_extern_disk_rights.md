---
title: "USB extern disk rights?"
date: 2005-03-26
forum: General Help
---

### Post by Fred on 2005-03-26
Hello,

I use a Hoary 5.04
I ve got a problem with the ftp user..
i want him to go on my usb extern disk
but he can't because he dont have any rights to go there...
the rights are only for my main user (fred)
i use the kernel ubuntu package & the kernel-headers ubuntu package
how can i do this?

thank you for your help!

Fred l alambique

---

### Post by alastair on 2005-03-26
I guess if you also have a group "fred", and have group permissions for "fred" on the USB drive, you could add user "ftp" to group "fred"?

---

