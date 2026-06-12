---
title: "PGP passphrase not accepted"
date: 2015-03-25
forum: General Help
---

### Post by cathect2 on 2015-03-25
On my desktop computer, running Ubuntu 14.04 I have a private key that I use to encrypt files and email. I can encrypt and decrypt there without issue. 

However, when I attempt to decrypt a file on a separate laptop, my passphrase is not accepted. The same problem occurs when attempting to use Enigmail to decrypt an email message with the same key: the desktop functions as expected, the laptop rejects the passphrase. 

I am dead certain that I'm using the proper key and passphrase.

I'm at a loss. There seems to be something buggy going on, but I haven't seen any discussion of this. Anyone have an idea of how to clear this?

Thanks!

---

### Post by cathect2 on 2015-03-25
So, I went into Startup Applications and unchecked GPG Password Agent. After restarting, my password was accepted and I was able to decrypt. But, after the passphrase gets cached, it gives me the same error.

Why is this happening? Some kind of conflict?

---

