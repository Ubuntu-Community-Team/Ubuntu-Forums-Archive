---
title: "wubi stuck on boot"
date: 2007-05-11
forum: General Help
---

### Post by psychoboogie on 2007-05-11
just installed the latest wubi on my oqo 02.

it sarts up gets to boot

then gets an error

Int 6: CR2 00000000 err 00000000 EIP c03eb1c8 CS 00000060 flags 000100012
Stack: 00000014 000000000 c03ddc03 c0126c2b c0363cc7 c03d3fbc c03d3fe8 c03de0d0


any thoughts?

thx

---

### Post by ago on 2007-05-11
I do not think that your processor is supported by current kernel, a special kernel might have to be used and lupin recompiled to use that.

---

### Post by psychoboogie on 2007-05-11
makes sense....

hope that it gets added in the future.

---

### Post by Donald F. Robertson on 2007-06-04
I just tried the same thing some three months later, and got a similar response.  I hope that our processor gets supported sometime soon.

However, if the processor is the problem, I wonder why I can run Ubuntu from the live CD. . . ?

-- Donald

---

### Post by ago on 2007-06-04
If you can run from live cd then it's some other issue. But it's difficult for me to debug without an oqo, if you guys send me one, I'll add wubi support ;P

---

### Post by Donald F. Robertson on 2007-06-04
I'd love to send you one, but I doubt I could obtain a surplus machine.

That said, OQO's Web site provides an individual ias the contact point for Linux development,

[http://support.oqo.com/cgi-bin/oqo.cfg/php/enduser/std_adp.php?p_faqid=547&p_created=1169519765&p_sid=Wl_xPiDi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NSZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9bGludXg*&p_li=&p_topview=1](http://support.oqo.com/cgi-bin/oqo.cfg/php/enduser/std_adp.php?p_faqid=547&p_created=1169519765&p_sid=Wl_xPiDi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NSZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9bGludXg*&p_li=&p_topview=1)

They also provide this info for an earlier version of the machine with a different processor, on which standard Ubuntu works fine.

"OQO is, however, actively contributing to the Linux-on-OQO and we have provided some Ubuntu packages.   Check out the following links for more details:

Information:       [ftp://ftp.oqo.com/unsupported/linux/OQOLinux.html](ftp://ftp.oqo.com/unsupported/linux/OQOLinux.html)
Files and prebuilt kernel packages:       [ftp://ftp.oqo.com/unsupported/linux](ftp://ftp.oqo.com/unsupported/linux)


Specifications are here,

[http://www.oqo.com/products/model02/specifications.html](http://www.oqo.com/products/model02/specifications.html)

[http://www.via.com.tw/en/products/processors/c7-m_ulv/](http://www.via.com.tw/en/products/processors/c7-m_ulv/)

---

