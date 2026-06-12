---
title: "cryptmount LUKS password prompt during boot 13.10"
date: 2013-12-26
forum: General Help
---

### Post by akos.maroy on 2013-12-26
Hi,

I recenlty upgraded to 13.10, and I have a strange behaviour. I have a LUKS partition that I open with a password prompt. Previously, I simply specified the details of this partition in /etc/cryttab, and during book, I was asked for the password of the LUKS partition, and everything worked fine.

Now in 13.10, cryttab doesn't seem to work anymore. I saw there is something called crytmount, so I set up the details in /etc/cryptmount/cmtab. this seems to work fine when starting manually, but during boot what happens is that I get all the way through the visual log in window, without a password prompt appearing. now, if I CTRL-F7 to the text console, I actually see the password prompt.

but, well, this seems to be less of a behaviour than earlier. is there a way to 'fix' this and make it work as it used to?


Akos

---

