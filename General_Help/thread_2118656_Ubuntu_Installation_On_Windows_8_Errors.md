---
title: "Ubuntu Installation On Windows 8 Errors"
date: 2013-02-21
forum: General Help
---

### Post by jnLink on 2013-02-21
I used the wubi, it appeared successful. Then I used the windows 8 boot thingy (apparently there is no BIOS) and chose other operating system. I then picked UBUNTU and it errored with a winboot thing. It appeared as if it thought it was a broken windows operating system. Help?

---

### Post by JiuJitsu500 on 2013-02-21
Make sure Secure boot is OFF.

You don't have a BIOS likely, newer PC's with windows 8 ship with UEFI like Mac's have had for a while. UEFI boots things different too (kind of), and you likely have GPT which Ubuntu doesn't like. From Wubi, this isn't usually an issue unless Secure Boot is on, then it will only let you boot from Windows 8.

---

### Post by bcbc on 2013-02-22
Wubi doesn't work on any computer booting with UEFI. This includes any new computer that ships with Windows 8. Turning off secure boot won't help. It doesn't work and there is no workaround to make it work.

Your options are normal dual boot or a VM.

[https://bugs.launchpad.net/wubi/+bug/694242](https://bugs.launchpad.net/wubi/+bug/694242)

---

