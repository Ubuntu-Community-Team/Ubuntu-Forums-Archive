---
title: "&quot;drive for /tmp is not ready&quot;"
date: 2014-04-01
forum: General Help
---

### Post by Ertai87 on 2014-04-01
When I boot my computer (12.04, only 1 HD in the machine) I get the above error message.  Why and what can I do to fix it?  Thanks.

---

### Post by sudodus on 2014-04-02
***/tmp*** is a directory for writing temporary files, that has a standard name and is used by several programs.

If the Ubuntu system works, just complains, I think it is because the drive has not been started completely, when /tmp is needed the first time. So it complains, and maybe waits a while and then /tmp is available. When Ubuntu is running, you can browse to the /tmp directory . I think it is there, otherwise the system would not work.

But if the system does not work, but stops at that message, we have to search for the error.

---

### Post by Ertai87 on 2014-04-02
The computer works fine, its just annoying, and it's never happened before (I've installed Ubuntu on multiple computers in my time).  My computer only has 1 drive (well 2 including a CD-Rom drive), so how can it not be started?

---

### Post by sudodus on 2014-04-03
Yes, I agree it is annoying, but I have no solution, except maybe to make it wait long at the grub menu before continuing (and hope the drive will be ready, when asked for the temporary directory). But it is more annoying to have to wait those extra seconds ...

---

### Post by CaptainMark on 2014-04-03
Do you have encrypted home directories? If you chose to encrypt your home directory during install it also encrypts /tmp for security whilst the computer is off, slower computers (my laptop included) take a while during to boot to decrypt /tmp and the system just has to wait until its ready. This may not be the cause for you but it's a possibility worth mentioning

---

### Post by Ertai87 on 2014-04-03
I don't think I have encrypted home directories.  I recall not checking that box when I formatted the computer, but I could be mis-remembering.

---

