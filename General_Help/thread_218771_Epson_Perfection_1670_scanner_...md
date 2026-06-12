---
title: "Epson Perfection 1670 scanner .."
date: 2006-07-19
forum: General Help
---

### Post by Brighid on 2006-07-19
Hi everyone,

I've had Kubuntu going for a while, but I've only just now found the need to scan something, and I realized I don't know what to do.  So, I tried to remedy that ..

I found out that Kooka is the default application for scanning, so I ran it.  It seemed to detect my scanner (Epson Perfection 1670), but then it told me I didn't have a "SANE" installation.  So I went on Adept and installed the package called "sane".  It didn't do anything .. so I thought I had to configure it, but typing "sane" in the terminal didn't work.

So I read that "xsane" is another program I could use, and I tried that, but it gave me an error window:

```
Failed to open device `snapscan:libusb:001:003':
Invalid argument.
```

In the terminal it said:

```
Failed to open device
[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
```

So I went to /usr/share/sane/ .. but there was no snapscan folder.

So I thought maybe I needed a package called snapscan, but there's no such thing on Adept.

I don't know what to do now ..

I love Linux, but things are always so painfully complicated ..

Well, if anyone has any ideas, please share.  Thank you.

---

