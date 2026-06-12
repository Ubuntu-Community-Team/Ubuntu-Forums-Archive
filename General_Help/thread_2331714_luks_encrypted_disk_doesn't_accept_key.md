---
title: "luks encrypted disk doesn't accept key"
date: 2016-07-25
forum: General Help
---

### Post by h4ml3t on 2016-07-25
Hello everyone. I registered because I have a problem I can't find a solution on the web. Installing ubuntu 16.04 from the usb, I encrypted my main disk with luks and used a password I remember perfectly. As this is the main hard disk, I can't use windows anymore, because the disk containing it is encrypted. I tried to decrypt but it won't accept my key, and I'm 200% it's right. I made a little research on internet and found out that the keyboard may be the cause of all it. So I changed my keyboard layout to English (US) and tried to decrypt without success.

I used that to decrypt the disk:

```
 cryptsetup luksOpen /dev/disk cryptdisk 
```

and it answered me:

```
 no key available with this passphrase 
```

I hope you can help me because I need to use a lot of the files stored in there. As I'm beginning using linux, I'd appreciate if you guide me step by step. Lot of thanks!

---

### Post by h4ml3t on 2016-07-26
Please, I need help. I'm not able to use my windows account :/

---

### Post by h4ml3t on 2016-07-27
Anybody can help me? Please!

---

