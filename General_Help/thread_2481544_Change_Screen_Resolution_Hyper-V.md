---
title: "Change Screen Resolution Hyper-V"
date: 2022-12-02
forum: General Help
---

### Post by matthew-cats-dogs on 2022-12-02
How do you change the screen resolution to 1920x 1080 in a Ubuntu Desktop 22.04 virtual machine using Windows 11 Pro and Hyper-V?

---

### Post by MAFoElffen on 2022-12-02
Edit file /etc/default//grub with sudo permissions, and change this line 
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


```
to resemble:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"

```
Uncomment and change this line
```

GRUB_GFXMODE=1920x1080x24

```
Save, exit, then do
```

sudo update grub
sudo reboot

```

---

### Post by MAFoElffen on 2022-12-02
Alternately, if you install and configure 'xrdp' in Ubuntu, when you connect to the VM, it will ask what resolution you want it to be in...

alibi, in Powershell
```

Get-VM
Set-VM -VMName "The_VM_Name" -EnhancedSessionTransportType HvSocket

```

---

### Post by matthew-cats-dogs on 2022-12-04
Thanks!

---

