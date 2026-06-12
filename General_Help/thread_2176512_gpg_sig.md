---
title: "gpg sig"
date: 2013-09-24
forum: General Help
---

### Post by garejnc on 2013-09-24
Hello!

I have, with my tiny brain managed to figure out, that signing a file can be done with gpg -s <file>. But, that output is AFAI can see binary. I would like to have those nice ASCII signatures like:
> -----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.12 (GNU/Linux)

iQEcBAABAgAGBQJSQfobAAoJEH5rYO3T1lOOPeEH/RqNxBlMmbslUwDi2kBso/mA
9F2IZUy8GO//+w5hsJNNoffn+b0/5ZO/rb+q9SpWdWsuXV1jNRf+9wMGShAsUIAE
eTlAIFS9AGrsgHBiVLyAwouA8TTef2UbvEAm+HZy9kTDlicgrtMJcBLvaDZnvm5I
8SdV97S4S+85/EIWW+2gUgDbIpCGfG5iPuqJD8Uz8by/acS+YWuNK1zcCXOpj30Z
Nx9D6m1LkMUJCYohnTdI/hpJ2RPi95hzre8i2jBpoxpRdOpVHQvNwaDJ8Y8aTOZo
ed6WOlnETW3VJ9QDKAJ1gKeRa+03Iuj1+J6hjnlRasNBLO28afwGz6+sWFKcQ94=
=f2zm
-----END PGP SIGNATURE-----

How is that done? (other tne parsing through binary file and generating it manually)

---

### Post by Impavidus on 2013-09-25
Try **gpg -a -s <file>**. -a or --armor means ascii armour the output.

---

