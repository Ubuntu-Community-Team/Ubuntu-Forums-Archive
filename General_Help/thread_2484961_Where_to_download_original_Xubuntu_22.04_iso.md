---
title: "Where to download original Xubuntu 22.04 iso?"
date: 2023-03-15
forum: General Help
---

### Post by &amp;KyT$0P# on 2023-03-15
Like the title says.  Where to download the original Xubuntu 22.04 iso, i.e. "Xubuntu 22.04.0"?  [https://cdimage.ubuntu.com/](https://cdimage.ubuntu.com/) only offers 22.04.2 in **all** the 22.04.x folders, and [https://old-releases.ubuntu.com/releases/xubuntu/releases/](https://old-releases.ubuntu.com/releases/xubuntu/releases/) doesn't seem to have any old Xubuntu 22.04 point releases?

(Actually, I might already have the iso.  So first would like to get the SHA256sums and SHA256sums.gpg files for original Xubuntu 22.04 iso, to check whether what I have on hand is indeed the correct one.  Assuming those would be available in the same place as the iso.)

Thanks

---

### Post by MAFoElffen on 2023-03-15
I searched through the repos... I think I found it for you: [https://cdimage.ubuntu.com/xubuntu/releases/](https://cdimage.ubuntu.com/xubuntu/releases/)

Specifically for the original Xubuntu 22.04: [https://cdimage.ubuntu.com/xubuntu/releases/22.04/release/](https://cdimage.ubuntu.com/xubuntu/releases/22.04/release/)

---

### Post by grahammechanical on 2023-03-15
I tried looking for it an hour or two ago and I kept getting redirected to Xubuntu 22.04.2 LTS. As you can see when I follow through on the link that you have provided.

[https://cdimage.ubuntu.com/xubuntu/releases/22.04.1/release/](https://cdimage.ubuntu.com/xubuntu/releases/22.04.1/release/)

It is the download page for Xubuntu 22.04.2. For some reason the Xubuntu developers do not want people to now download Xubuntu 22.04.1.

Regards

---

### Post by MAFoElffen on 2023-03-15
> **grahammechanical said:**
> I tried looking for it an hour or two ago and I kept getting redirected to Xubuntu 22.04.2 LTS. As you can see when I follow through on the link that you have provided.

[https://cdimage.ubuntu.com/xubuntu/releases/22.04.1/release/](https://cdimage.ubuntu.com/xubuntu/releases/22.04.1/release/)

It is the download page for Xubuntu 22.04.2. For some reason the Xubuntu developers do not want people to now download Xubuntu 22.04.1.

Regards
Doh!!! I see that now...

With just a little hacking (I tried): [https://cdimage.ubuntu.com/xubuntu/releases/22.04/release/SHA256SUMS](https://cdimage.ubuntu.com/xubuntu/releases/22.04/release/SHA256SUMS)

Dang, that redirects also...
```

c7072859113399bef0e680a08c987c360f41642d8089ebb8928689066a9c9759 *xubuntu-[COLOR=#FF0000]22.04.2[/COLOR]-desktop-amd64.iso

```
I tried Wayback TimeMachine and it failed also. Sorry. LOL

---

### Post by &amp;KyT$0P# on 2023-03-15
> **MAFoElffen said:**
> I tried Wayback TimeMachine and it failed also. 

Not for me it didn't fail, thanks for the suggestion MAFoElffen! :KS

[SHA256SUMS]("https://web.archive.org/web/20220808193620/https://cdimage.ubuntu.com/xubuntu/releases/22.04/release/SHA256SUMS")
```
61a6e4df2f89782541e114cbb23dcde7ed8851ac0b013e952d2afd0094646c46 *xubuntu-22.04-desktop-amd64.iso
```

[SHA256SUMS.gpg]("https://web.archive.org/web/20220628065020/http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/xubuntu/releases/22.04/release/SHA256SUMS.gpg")
```
-----BEGIN PGP SIGNATURE-----

iQIzBAABCgAdFiEEhDk43yKNIvezdCvA2Uqj8O/iEJIFAmJhZA4ACgkQ2Uqj8O/i
EJLayRAAlLgu9QPHbRFf38D7fd0NGd9llpPRelXcQa0AtRBmaEc+5ktoBK3+h/4D
1Sh+vIAxcxPLl+a7yiaI12h8uwDcWdqvtnLLxPjsBU4ugopt/F3h6jRLSiMD92dx
AnHtB5OxzOyCOqNYH/UpOpj3lOBtYNo+yjvtWFJ5SLdAGkxuA+pgyfDBQwhnm2bI
xHCcaOcTjIfTY1p52ISCPfHsLA5gakvky2/bGcbHgRXiBVgh3IRcL6ntrDh0TNm/
vfc0mlhSPRb53dKffdShSYt40z+JUGnRzbK/fX3rz82t1IOVXgPwA8J3i64wPocW
pPWOb01wEwx+pwYm+uj58lkEuHIcMFMDCsapks5r3UVG9bP7FmYWi1BqA8mlcomE
ASLNXM3sbbiL8MJNEnTEWAIU8W+QKt+c74TxoFbVDbbaOKz2fjr3WcG12NgM4i9e
Zo19Jp6zGG5UTRciWQ6hFziHbb9sntV3A5+HdqLUwwgeuWS2O+SWz2J/xAQ2+R7i
KyTyBiYrxz43daFI/uxHYSAjGhp6AFOfnPg5vyHvIpxQgFGFr0hwF1Vgeqmd+5Nf
rpJtSIP5KMu7sgLS50SC1WbbET+dGD6KcDPduk298kfRPO595VAzBQUyhCA/m/yN
iMw5HYTMhYGGUiGG5Oef+MbZ2SvlVdwaXkphEySJrzNp/TwcNEU=
=6HYN
-----END PGP SIGNATURE-----

```

And checking the integrity gave -
```
$ gpg --keyring /etc/apt/trusted.gpg.d/ubuntu-keyring-2012-cdimage.gpg --verify SHA256SUMS.gpg SHA256SUMS
gpg: Signature made Thu 21 Apr 2022 10:02:54 AM EDT
gpg:                using RSA key 843938DF228D22F7B3742BC0D94AA3F0EFE21092
gpg: Good signature from "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" [unknown]
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092

```

And that SHA256 checksum is indeed the checksum of the iso I have on hand.

* Just discovered, when copy-pasting the SHA256SUMS into a file: the GPG verification requires that the one-line SHA256SUMS file must end with a newline character.

---

