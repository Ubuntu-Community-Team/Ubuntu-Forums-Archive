---
title: "Problems Signing The Code Of Conduct"
date: 2007-02-27
forum: General Help
---

### Post by ebozzz on 2007-02-27
Help! I having problems signing the code of conduct. I have already registered my OpenPGP key. I then downloaded the Code. 

After I read the code I attempted to sign it using the terminal. 

> gpg --clearsign UbuntuCodeofConduct-1.0.1.txt 

I am then asked for a pass phrase and after entering it I get this.....

> gpg: can't open `UbuntuCodeofConduct-1.0.1.txt': No such file or directory
gpg: UbuntuCodeofConduct-1.0.1.txt: clearsign failed: file open error

Can someone please tell me what I am doing wrong? :confused:

---

### Post by llamakc on 2007-02-27
You need to be in the same directory you downloaded the file to.

---

### Post by ebozzz on 2007-02-27
> **llamakc said:**
> You need to be in the same directory you downloaded the file to.

Thank you! It's all done.

---

