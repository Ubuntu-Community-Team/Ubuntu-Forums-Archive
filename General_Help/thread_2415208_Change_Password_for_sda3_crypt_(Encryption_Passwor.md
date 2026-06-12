---
title: "Change Password for sda3_crypt (Encryption Password)"
date: 2019-03-22
forum: General Help
---

### Post by scribner on 2019-03-22
Hi,

I was wondering if there is any simple way of changing Ubuntu's encryption password. If possible, please provide official documentation.

---

### Post by TheFu on 2019-03-22
That's luks which is part of dm-crypt. The tool to control that is **cryptsetup**.
There are 8 passphrase slots which can hold different passphrases to unlock the encrypted storage.

The official documentation is the manpage.  **man cryptsetup** will access it.```

       LUKS can manage multiple passphrases that can be  individually  revoked
       or  changed and that can be securely scrubbed from persistent media due
       to the use of anti-forensic stripes. Passphrases are protected  against
       brute-force  and  dictionary  attacks  by PBKDF2, which implements hash
       iteration and salting in one function.

       Each passphrase, also called a key in this document, is associated with
       one  of  8 key-slots.  Key operations that do not specify a slot affect
       the first slot that matches the supplied passphrase or the first  empty
       slot if a new passphrase is added.
```
Farther down ....```

       luksChangeKey <device> [<new key file>]

              Changes  an  existing  passphrase.  The passphrase to be changed
              must be supplied  interactively  or  via  --key-file.   The  new
              passphrase  can  be supplied interactively or in a file given as
              positional argument.

              If a key-slot is specified (via --key-slot), the passphrase  for
              that  key-slot  must  be given and the new passphrase will overâ
              write the specified key-slot. If no key-slot  is  specified  and
              there  is still a free key-slot, then the new passphrase will be
              put into a free key-slot before the key-slot containing the  old
              passphrase  is  purged.  If  there is no free key-slot, then the
              key-slot with the old passphrase is overwritten directly.
....
       --key-slot, -S <0-7>
              For LUKS operations that add key material, this  options  allows
              you to specify which key slot is selected for the new key.  This
              option can be used for luksFormat, and luksAddKey.
              In addition, for open, this option selects a  specific  key-slot
              to  compare  the  passphrase  against.   If the given passphrase
              would only match a different key-slot, the operation fails.


``` It continues.
Hope this helps.  The manpages are pretty good for this command.

---

