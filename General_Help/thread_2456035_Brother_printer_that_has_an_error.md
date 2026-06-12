---
title: "Brother printer that has an error"
date: 2021-01-02
forum: General Help
---

### Post by SUPERFITTER on 2021-01-02
I have a Brother printer that has an error that says I am missing this: /usr/lib/cups/filter/rastertogutenprint.5.3

How do I fix this?

Thank You

---

### Post by grahammechanical on 2021-01-02
It is a printer driver that you need to install. See the Install Howto section of this link

[https://ubuntu.pkgs.org/20.04/ubuntu-main-arm64/printer-driver-gutenprint_5.3.3-4_arm64.deb.html](https://ubuntu.pkgs.org/20.04/ubuntu-main-arm64/printer-driver-gutenprint_5.3.3-4_arm64.deb.html)

>  
[LIST=1]
[*]Update the package index: # sudo apt-get update
[*]Install printer-driver-gutenprint deb package: # sudo apt-get install printer-driver-gutenprint
[/LIST]

Regards

---

### Post by TheFu on 2021-01-02
> **SUPERFITTER said:**
> I have a Brother printer that has an error that says I am missing this: /usr/lib/cups/filter/rastertogutenprint.5.3

How do I fix this?

Thank You

To find out which package provides a file, there are a few APT commands that can do that.
```
$ dpkg -S /usr/lib/cups/filter/rastertogutenprint.5.3
```
or
```
$ dpkg-query --search '/usr/lib/cups/filter/rastertogutenprint.5.2'
```

These appear to have the exact same output. I'd use the first. Less to type, no single-quotes needed.

---

