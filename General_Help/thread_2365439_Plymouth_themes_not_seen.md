---
title: "Plymouth themes not seen"
date: 2017-07-06
forum: General Help
---

### Post by payasam on 2017-07-06
Despite having eighteen theme folders under /usr/share/plymouth/themes/, update-alternatives offers me only three choices. Is it looking in the wrong place?

---

### Post by Dennis N on 2017-07-06
> **payasam said:**
> Despite having eighteen theme folders under /usr/share/plymouth/themes/, update-alternatives offers me only three choices. Is it looking in the wrong place?

Most likely, they are not installed.

Installed themes in my current OS (theme names are actually the folder name, like **spinner**):
```
dmn@Roxanne:~$ update-alternatives --list default.plymouth
/usr/share/plymouth/themes/spinner/spinner.plymouth
/usr/share/plymouth/themes/ubuntu-budgie-logo/budgie-logo-scale-2.plymouth
/usr/share/plymouth/themes/ubuntu-budgie-logo/budgie-logo.plymouth
```
Install a new theme **solar** from themes in the themes folder:
```
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/solar/solar.plymouth 20

```
run 
```
sudo update-alternatives --config default.plymouth
```
and select the new theme.
Last, update initramfs
```
sudo update-initramfs -u
```

---

### Post by payasam on 2017-07-06
Thank you, Dennis. It would not have occurred to me that files which were in the right place were still not installed.

---

