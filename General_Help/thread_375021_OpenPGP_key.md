---
title: "OpenPGP key"
date: 2007-03-03
forum: General Help
---

### Post by Thomas Delbeke on 2007-03-03
Hi, 

I need to confirm an openPGP key so I can sign the Ubuntu code of conduct. When I open GnomePGP and paste the message I received by email in the terminal, it does nothing when I press decrypt. Somehow I guess I need to decrypt the message by using my key, but I don't know how:( .

Thanks in advance,

Thomas

---

### Post by Kateikyoushi on 2007-03-03
Try this of course save the text to file.

```
gpg --output cleartext.txt --decrypt encrypted_message.txt
```

---

### Post by Thomas Delbeke on 2007-03-04
OK, thanks alot!

Thomas

---

