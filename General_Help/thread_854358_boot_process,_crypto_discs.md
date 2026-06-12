---
title: "boot process, crypto discs"
date: 2008-07-09
forum: General Help
---

### Post by mriedel on 2008-07-09
Could anyone point me to a resource where i can read up on the ubuntu boot process, especially on when and how early (and other) cryptodiscs are mounted (early as in encrypted LVM, other as in remaining non-system drives) and how to modify it? This probably involves how the initramfs is created and what exactly update-initramfs does.

---

### Post by mriedel on 2008-07-10
To be more specific, I'm running full disc encryption with an encrypted LVM. Currently, I decrypt it with a plaintext keyfile on an usb stick which is temporarily mounted in the initramfs using a script. Now I want to encrypt the usb stick and have it decrypted and mounted when/after the initramfs is created and then use the keyfile to decrypt the LVM and another hdd. In this case I'd prefer knowing what I'm doing over trial and error, so this is why I'm asking.

---

### Post by mriedel on 2008-07-11
bump

---

### Post by mriedel on 2008-07-13
bump

---

### Post by mriedel on 2008-07-15
bump

---

