---
title: "errors listed during boot before login"
date: 2007-02-15
forum: General Help
---

### Post by wxnker on 2007-02-15
During boot Ubuntu edgy shows some errors, but I cannot write them down in the few seconds they are shown. 

The first error looks like this: 
[17179579.544000] usb 1-1: device not accepting address 2, error -71

It also shows some codec errors and a ntfs utf8 error , I think

Where can I find the **"boot message error log"** or information about these errors from within Ubuntu edgy? [COLOR="Red"](solved this part => dmesg)[/COLOR]

---

### Post by wxnker on 2007-02-15
I got the errors written down by doing a couple of restarts, and then running "dmesg"

From dmesg:
[17179579.748000] usb 1-1: device not accepting address 2, error -71
[17179590.744000] codec_read: codec 0 is not valid [0xfe0000]
[17179590.752000] codec_read: codec 0 is not valid [0xfe0000]
[17179590.756000] codec_read: codec 0 is not valid [0xfe0000]
[17179590.764000] codec_read: codec 0 is not valid [0xfe0000]

I think the codec errors are related to my soundblaster live soundcard.

I fixed the NTFS error by editing "fstab" and I guess the remaining errors are merely cosmetic because Ubuntu runs fine. It slows boot up though, so I'd like to solve them or maybe make ubuntu ignore them during boot.

---

