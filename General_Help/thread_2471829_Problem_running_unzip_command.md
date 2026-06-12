---
title: "Problem running unzip command"
date: 2022-02-10
forum: General Help
---

### Post by satimis on 2022-02-10
Hi all,

$ unzip DaVinci_Resolve_17.4.3_Linux.zip```

Archive:  DaVinci_Resolve_17.4.3_Linux.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of DaVinci_Resolve_17.4.3_Linux.zip or
        DaVinci_Resolve_17.4.3_Linux.zip.zip, and cannot find DaVinci_Resolve_17.4.3_Linux.zip.ZIP, period.

```

I have download DaVinci_Resolve_17.4.3_Linux.zip twice.  Problem still remain.

Pls advise.  Thanks

Regards

---

### Post by &amp;KyT$0P# on 2022-02-10
Please post the output from running the following command in Terminal -
```
file DaVinci_Resolve_17.4.3_Linux.zip
```

---

### Post by satimis on 2022-02-10
> **halogen2 said:**
> Please post the output from running the following command in Terminal -
```
file DaVinci_Resolve_17.4.3_Linux.zip
```
Hi,

The output has been posted on my op above.  The Linux package was download on blackmagicdesign website;

[https://www.blackmagicdesign.com/products/davinciresolve/](https://www.blackmagicdesign.com/products/davinciresolve/)

I tested it on Ubuntu 20.04 VM of Oracle VirtualBox.

They have Windows package.  I have download and installed it on both Win10 VM of Oracle VirtualBox and Win10 Guest of KVM/Qemu.  Installation went through without problem but it can't work because GPU can't be forward to VM/Guest from Host.  I'm prepared to try it on Win10 running on bare-metal SSD.

I suppose its Linux version can't work on VM/Guest.  I'll test installing it on Ubuntu 20.04 running on bare-metal SSD

On my database I found following DaVinci Resolve packages of 2021 Oct.```

DaVinci_Resolve_17.3.2_Linux.zip
DaVinci_Resolve_17.3.2_Linux.run
davinci-resolve_17.3.2-mrd1.5.1_amd64.deb

```

Edit-1
===
Whether you meant running "file" command?  I'll test it later and come back after testing.  Thanks

Edit-2
====
1)
$ file DaVinci_Resolve_17.4.3_Linux.zip```

DaVinci_Resolve_17.4.3_Linux.zip: Zip archive data, at least v2.0 to extract

```

2)
Found Ubuntu 20.04 VM of Oracle VirtualBox
DaVinci Resolve 16.2.8 is running on it, installed on 26/10/2021.  But it can't work because GPU can't be forward to it from Host.  I think installing DaVinci Resolve on Ubuntu Guest of KVM/QEMU would encounter the same problem.

I have to install DaVinci Resolve on Ubuntu 20.04 running on bare-metal SSD

Regards

---

### Post by &amp;KyT$0P# on 2022-02-11
Can another tool unzip it, e.g. [FONT=Courier New]unar[/FONT] or a GUI archive manager such as file-roller?

---

### Post by satimis on 2022-02-12
> **halogen2 said:**
> Can another tool unzip it, e.g. [FONT=Courier New]unar[/FONT] or a GUI archive manager such as file-roller?
Problem solver by re-download another package today.

But encounter another problem on starting Davinci Resolve.  I have started a new posting.

Regards

---

