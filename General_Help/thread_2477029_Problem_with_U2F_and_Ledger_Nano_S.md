---
title: "Problem with U2F and Ledger Nano S"
date: 2022-07-12
forum: General Help
---

### Post by hobietime on 2022-07-12
Hello.

I have been having difficulty using My Ledger Nano S Plus with the Snap versions Firefox and Chromium on Xubuntu 22.04 LTS.

I have found these threads/help and ended up with no luck when trying to remediate the issue.

[https://www.sindastra.de/p/1259/fix-fido-u2f-linux](https://www.sindastra.de/p/1259/fix-fido-u2f-linux)

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1947746/](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1947746/)

This is the demo website I have been using to test. 

[https://demo.yubico.com/webauthn-technical/registration](https://demo.yubico.com/webauthn-technical/registration)

It times out with his error:

```
The request is not allowed by the user agent or the platform in the  current context, possibly because the user denied permission.
```

I have attached my udev file in case I messed anything up. 

Is there anything I am missing here?


EDIT TO ADD:

I have confirmed this key works with Chome on Windows 10, as well as confirmed with ```
fido2-token -L
/dev/hidraw5: vendor=0x2c97, product=0x5005 (Ledger Nano S Plus)
``` that the hardware key is recognized.

---

