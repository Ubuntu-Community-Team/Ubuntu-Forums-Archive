---
title: "booting ubuntu sever iso via grub loopback"
date: 2014-08-21
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-08-21
with the desktop iso files i use these 2 lines
```
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
```
there is no casper folder on the server iso, what should i use for this part?
here is the entire segment i have on my usb for 14.04
```
submenu 'Ubuntu 14.04.1' --class submenu --id trusty {
    submenu 'Ubuntu 14.04.1 32bit' --class submenu --id trusty_32 {
        menuentry "Xubuntu 14.04.1 Desktop 32bit" --class xubuntu --class gnu-linux --id trusty_32 {
            set isofile="/iso/Trusty/xubuntu-14.04.1-desktop-i386.iso"
            loopback loop $isofile
            linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt splash --
            initrd (loop)/casper/initrd.lz
        }
    }
    menuentry "Ubuntu 14.04.1 Desktop 64bit" --class ubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/ubuntu-14.04.1-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Xubuntu 14.04.1 Desktop 64bit" --class xubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/xubuntu-14.04.1-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Ubuntu Gnome 14.04.1 Desktop 64bit" --class gnomeubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/ubuntu-gnome-14.04.1-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Kubuntu 14.04.1 Desktop 64bit" --class kubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/kubuntu-14.04.1-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Lubuntu 14.04.1 Desktop 64bit" --class lubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/lubuntu-14.04.1-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Ubuntu 14.04.1 Server 64bit" --class ubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/ubuntu-14.04.1-server-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
}
```
here are teh files in the iso
```
tree -L 3 /tmp/iso/
/tmp/iso/
&#9500;&#9472;&#9472; boot
&#9474;   &#9492;&#9472;&#9472; grub
&#9474;       &#9500;&#9472;&#9472; efi.img
&#9474;       &#9500;&#9472;&#9472; font.pf2
&#9474;       &#9500;&#9472;&#9472; grub.cfg
&#9474;       &#9500;&#9472;&#9472; loopback.cfg
&#9474;       &#9492;&#9472;&#9472; x86_64-efi
&#9500;&#9472;&#9472; dists
&#9474;   &#9500;&#9472;&#9472; stable -> trusty
&#9474;   &#9500;&#9472;&#9472; trusty
&#9474;   &#9474;   &#9500;&#9472;&#9472; main
&#9474;   &#9474;   &#9500;&#9472;&#9472; Release
&#9474;   &#9474;   &#9500;&#9472;&#9472; Release.gpg
&#9474;   &#9474;   &#9492;&#9472;&#9472; restricted
&#9474;   &#9492;&#9472;&#9472; unstable -> trusty
&#9500;&#9472;&#9472; doc
&#9474;   &#9492;&#9472;&#9472; install
&#9474;       &#9492;&#9472;&#9472; manual
&#9500;&#9472;&#9472; EFI
&#9474;   &#9492;&#9472;&#9472; BOOT
&#9474;       &#9500;&#9472;&#9472; BOOTx64.EFI
&#9474;       &#9492;&#9472;&#9472; grubx64.efi
&#9500;&#9472;&#9472; install
&#9474;   &#9500;&#9472;&#9472; filesystem.manifest
&#9474;   &#9500;&#9472;&#9472; filesystem.size
&#9474;   &#9500;&#9472;&#9472; filesystem.squashfs
&#9474;   &#9500;&#9472;&#9472; initrd.gz
&#9474;   &#9500;&#9472;&#9472; mt86plus
&#9474;   &#9500;&#9472;&#9472; netboot
&#9474;   &#9474;   &#9500;&#9472;&#9472; pxelinux.0 -> ubuntu-installer/amd64/pxelinux.0
&#9474;   &#9474;   &#9500;&#9472;&#9472; pxelinux.cfg -> ubuntu-installer/amd64/pxelinux.cfg
&#9474;   &#9474;   &#9500;&#9472;&#9472; ubuntu-installer
&#9474;   &#9474;   &#9492;&#9472;&#9472; version.info
&#9474;   &#9500;&#9472;&#9472; README.sbm
&#9474;   &#9500;&#9472;&#9472; sbm.bin
&#9474;   &#9492;&#9472;&#9472; vmlinuz
&#9500;&#9472;&#9472; isolinux
&#9474;   &#9500;&#9472;&#9472; 16x16.fnt
&#9474;   &#9500;&#9472;&#9472; adtxt.cfg
&#9474;   &#9500;&#9472;&#9472; am.tr
&#9474;   &#9500;&#9472;&#9472; ast.hlp
&#9474;   &#9500;&#9472;&#9472; ast.tr
&#9474;   &#9500;&#9472;&#9472; back.jpg
&#9474;   &#9500;&#9472;&#9472; be.hlp
&#9474;   &#9500;&#9472;&#9472; be.tr
&#9474;   &#9500;&#9472;&#9472; bg.hlp
&#9474;   &#9500;&#9472;&#9472; bg.tr
&#9474;   &#9500;&#9472;&#9472; bn.hlp
&#9474;   &#9500;&#9472;&#9472; boot.cat
&#9474;   &#9500;&#9472;&#9472; bootlogo
&#9474;   &#9500;&#9472;&#9472; bs.hlp
&#9474;   &#9500;&#9472;&#9472; bs.tr
&#9474;   &#9500;&#9472;&#9472; ca.hlp
&#9474;   &#9500;&#9472;&#9472; ca.tr
&#9474;   &#9500;&#9472;&#9472; chain.c32
&#9474;   &#9500;&#9472;&#9472; cs.hlp
&#9474;   &#9500;&#9472;&#9472; cs.tr
&#9474;   &#9500;&#9472;&#9472; da.hlp
&#9474;   &#9500;&#9472;&#9472; da.tr
&#9474;   &#9500;&#9472;&#9472; de.hlp
&#9474;   &#9500;&#9472;&#9472; de.tr
&#9474;   &#9500;&#9472;&#9472; dtmenu.cfg
&#9474;   &#9500;&#9472;&#9472; el.hlp
&#9474;   &#9500;&#9472;&#9472; el.tr
&#9474;   &#9500;&#9472;&#9472; en.hlp
&#9474;   &#9500;&#9472;&#9472; en.tr
&#9474;   &#9500;&#9472;&#9472; eo.hlp
&#9474;   &#9500;&#9472;&#9472; eo.tr
&#9474;   &#9500;&#9472;&#9472; es.hlp
&#9474;   &#9500;&#9472;&#9472; es.tr
&#9474;   &#9500;&#9472;&#9472; et.hlp
&#9474;   &#9500;&#9472;&#9472; et.tr
&#9474;   &#9500;&#9472;&#9472; eu.hlp
&#9474;   &#9500;&#9472;&#9472; eu.tr
&#9474;   &#9500;&#9472;&#9472; exithelp.cfg
&#9474;   &#9500;&#9472;&#9472; f10.txt
&#9474;   &#9500;&#9472;&#9472; f1.txt
&#9474;   &#9500;&#9472;&#9472; f2.txt
&#9474;   &#9500;&#9472;&#9472; f3.txt
&#9474;   &#9500;&#9472;&#9472; f4.txt
&#9474;   &#9500;&#9472;&#9472; f5.txt
&#9474;   &#9500;&#9472;&#9472; f6.txt
&#9474;   &#9500;&#9472;&#9472; f7.txt
&#9474;   &#9500;&#9472;&#9472; f8.txt
&#9474;   &#9500;&#9472;&#9472; f9.txt
&#9474;   &#9500;&#9472;&#9472; fa.tr
&#9474;   &#9500;&#9472;&#9472; fi.hlp
&#9474;   &#9500;&#9472;&#9472; fi.tr
&#9474;   &#9500;&#9472;&#9472; fr.hlp
&#9474;   &#9500;&#9472;&#9472; fr.tr
&#9474;   &#9500;&#9472;&#9472; ga.tr
&#9474;   &#9500;&#9472;&#9472; gfxboot.c32
&#9474;   &#9500;&#9472;&#9472; gfxboot.cfg
&#9474;   &#9500;&#9472;&#9472; gl.hlp
&#9474;   &#9500;&#9472;&#9472; gl.tr
&#9474;   &#9500;&#9472;&#9472; he.hlp
&#9474;   &#9500;&#9472;&#9472; he.tr
&#9474;   &#9500;&#9472;&#9472; hi.hlp
&#9474;   &#9500;&#9472;&#9472; hr.tr
&#9474;   &#9500;&#9472;&#9472; hu.hlp
&#9474;   &#9500;&#9472;&#9472; hu.tr
&#9474;   &#9500;&#9472;&#9472; id.hlp
&#9474;   &#9500;&#9472;&#9472; id.tr
&#9474;   &#9500;&#9472;&#9472; is.hlp
&#9474;   &#9500;&#9472;&#9472; isolinux.bin
&#9474;   &#9500;&#9472;&#9472; isolinux.cfg
&#9474;   &#9500;&#9472;&#9472; is.tr
&#9474;   &#9500;&#9472;&#9472; it.hlp
&#9474;   &#9500;&#9472;&#9472; it.tr
&#9474;   &#9500;&#9472;&#9472; ja.hlp
&#9474;   &#9500;&#9472;&#9472; ja.tr
&#9474;   &#9500;&#9472;&#9472; ka.hlp
&#9474;   &#9500;&#9472;&#9472; ka.tr
&#9474;   &#9500;&#9472;&#9472; kk.hlp
&#9474;   &#9500;&#9472;&#9472; kk.tr
&#9474;   &#9500;&#9472;&#9472; km.hlp
&#9474;   &#9500;&#9472;&#9472; kn.tr
&#9474;   &#9500;&#9472;&#9472; ko.hlp
&#9474;   &#9500;&#9472;&#9472; ko.tr
&#9474;   &#9500;&#9472;&#9472; ku.tr
&#9474;   &#9500;&#9472;&#9472; langlist
&#9474;   &#9500;&#9472;&#9472; lo.tr
&#9474;   &#9500;&#9472;&#9472; lt.hlp
&#9474;   &#9500;&#9472;&#9472; lt.tr
&#9474;   &#9500;&#9472;&#9472; lv.hlp
&#9474;   &#9500;&#9472;&#9472; lv.tr
&#9474;   &#9500;&#9472;&#9472; menu.cfg
&#9474;   &#9500;&#9472;&#9472; mk.tr
&#9474;   &#9500;&#9472;&#9472; mr.tr
&#9474;   &#9500;&#9472;&#9472; nb.hlp
&#9474;   &#9500;&#9472;&#9472; nb.tr
&#9474;   &#9500;&#9472;&#9472; nl.hlp
&#9474;   &#9500;&#9472;&#9472; nl.tr
&#9474;   &#9500;&#9472;&#9472; nn.hlp
&#9474;   &#9500;&#9472;&#9472; nn.tr
&#9474;   &#9500;&#9472;&#9472; pl.hlp
&#9474;   &#9500;&#9472;&#9472; pl.tr
&#9474;   &#9500;&#9472;&#9472; po4a.cfg
&#9474;   &#9500;&#9472;&#9472; prompt.cfg
&#9474;   &#9500;&#9472;&#9472; pt_BR.hlp
&#9474;   &#9500;&#9472;&#9472; pt_BR.tr
&#9474;   &#9500;&#9472;&#9472; pt.hlp
&#9474;   &#9500;&#9472;&#9472; pt.tr
&#9474;   &#9500;&#9472;&#9472; ro.hlp
&#9474;   &#9500;&#9472;&#9472; ro.tr
&#9474;   &#9500;&#9472;&#9472; rqtxt.cfg
&#9474;   &#9500;&#9472;&#9472; ru.hlp
&#9474;   &#9500;&#9472;&#9472; ru.tr
&#9474;   &#9500;&#9472;&#9472; si.hlp
&#9474;   &#9500;&#9472;&#9472; si.tr
&#9474;   &#9500;&#9472;&#9472; sk.hlp
&#9474;   &#9500;&#9472;&#9472; sk.tr
&#9474;   &#9500;&#9472;&#9472; sl.hlp
&#9474;   &#9500;&#9472;&#9472; sl.tr
&#9474;   &#9500;&#9472;&#9472; splash.pcx
&#9474;   &#9500;&#9472;&#9472; splash.png
&#9474;   &#9500;&#9472;&#9472; sq.hlp
&#9474;   &#9500;&#9472;&#9472; sq.tr
&#9474;   &#9500;&#9472;&#9472; sr.hlp
&#9474;   &#9500;&#9472;&#9472; sr.tr
&#9474;   &#9500;&#9472;&#9472; stdmenu.cfg
&#9474;   &#9500;&#9472;&#9472; sv.hlp
&#9474;   &#9500;&#9472;&#9472; sv.tr
&#9474;   &#9500;&#9472;&#9472; te.tr
&#9474;   &#9500;&#9472;&#9472; th.hlp
&#9474;   &#9500;&#9472;&#9472; tl.tr
&#9474;   &#9500;&#9472;&#9472; tr.hlp
&#9474;   &#9500;&#9472;&#9472; tr.tr
&#9474;   &#9500;&#9472;&#9472; txt.cfg
&#9474;   &#9500;&#9472;&#9472; ug.hlp
&#9474;   &#9500;&#9472;&#9472; uk.hlp
&#9474;   &#9500;&#9472;&#9472; uk.tr
&#9474;   &#9500;&#9472;&#9472; vesamenu.c32
&#9474;   &#9500;&#9472;&#9472; vi.hlp
&#9474;   &#9500;&#9472;&#9472; vi.tr
&#9474;   &#9500;&#9472;&#9472; zh_CN.hlp
&#9474;   &#9500;&#9472;&#9472; zh_CN.tr
&#9474;   &#9500;&#9472;&#9472; zh_TW.hlp
&#9474;   &#9492;&#9472;&#9472; zh_TW.tr
&#9500;&#9472;&#9472; md5sum.txt
&#9500;&#9472;&#9472; pics
&#9474;   &#9500;&#9472;&#9472; blue-lowerleft.png
&#9474;   &#9500;&#9472;&#9472; blue-lowerright.png
&#9474;   &#9500;&#9472;&#9472; blue-upperleft.png
&#9474;   &#9500;&#9472;&#9472; blue-upperright.png
&#9474;   &#9500;&#9472;&#9472; debian.jpg
&#9474;   &#9500;&#9472;&#9472; logo-50.jpg
&#9474;   &#9500;&#9472;&#9472; red-lowerleft.png
&#9474;   &#9500;&#9472;&#9472; red-lowerright.png
&#9474;   &#9500;&#9472;&#9472; red-upperleft.png
&#9474;   &#9492;&#9472;&#9472; red-upperright.png
&#9500;&#9472;&#9472; pool
&#9474;   &#9492;&#9472;&#9472; main
&#9474;       &#9500;&#9472;&#9472; a
&#9474;       &#9500;&#9472;&#9472; b
&#9474;       &#9500;&#9472;&#9472; c
&#9474;       &#9500;&#9472;&#9472; d
&#9474;       &#9500;&#9472;&#9472; e
&#9474;       &#9500;&#9472;&#9472; f
&#9474;       &#9500;&#9472;&#9472; g
&#9474;       &#9500;&#9472;&#9472; h
&#9474;       &#9500;&#9472;&#9472; i
&#9474;       &#9500;&#9472;&#9472; j
&#9474;       &#9500;&#9472;&#9472; k
&#9474;       &#9500;&#9472;&#9472; l
&#9474;       &#9500;&#9472;&#9472; liba
&#9474;       &#9500;&#9472;&#9472; libb
&#9474;       &#9500;&#9472;&#9472; libc
&#9474;       &#9500;&#9472;&#9472; libd
&#9474;       &#9500;&#9472;&#9472; libe
&#9474;       &#9500;&#9472;&#9472; libf
&#9474;       &#9500;&#9472;&#9472; libg
&#9474;       &#9500;&#9472;&#9472; libh
&#9474;       &#9500;&#9472;&#9472; libi
&#9474;       &#9500;&#9472;&#9472; libj
&#9474;       &#9500;&#9472;&#9472; libl
&#9474;       &#9500;&#9472;&#9472; libm
&#9474;       &#9500;&#9472;&#9472; libn
&#9474;       &#9500;&#9472;&#9472; libo
&#9474;       &#9500;&#9472;&#9472; libp
&#9474;       &#9500;&#9472;&#9472; libq
&#9474;       &#9500;&#9472;&#9472; libr
&#9474;       &#9500;&#9472;&#9472; libs
&#9474;       &#9500;&#9472;&#9472; libt
&#9474;       &#9500;&#9472;&#9472; libu
&#9474;       &#9500;&#9472;&#9472; libv
&#9474;       &#9500;&#9472;&#9472; libw
&#9474;       &#9500;&#9472;&#9472; libx
&#9474;       &#9500;&#9472;&#9472; liby
&#9474;       &#9500;&#9472;&#9472; m
&#9474;       &#9500;&#9472;&#9472; n
&#9474;       &#9500;&#9472;&#9472; o
&#9474;       &#9500;&#9472;&#9472; p
&#9474;       &#9500;&#9472;&#9472; q
&#9474;       &#9500;&#9472;&#9472; r
&#9474;       &#9500;&#9472;&#9472; s
&#9474;       &#9500;&#9472;&#9472; t
&#9474;       &#9500;&#9472;&#9472; u
&#9474;       &#9500;&#9472;&#9472; v
&#9474;       &#9500;&#9472;&#9472; w
&#9474;       &#9500;&#9472;&#9472; x
&#9474;       &#9500;&#9472;&#9472; y
&#9474;       &#9492;&#9472;&#9472; z
&#9500;&#9472;&#9472; preseed
&#9474;   &#9500;&#9472;&#9472; cli.seed
&#9474;   &#9500;&#9472;&#9472; cloud.seed
&#9474;   &#9500;&#9472;&#9472; ubuntu-server-minimal.seed
&#9474;   &#9500;&#9472;&#9472; ubuntu-server-minimalvm.seed
&#9474;   &#9492;&#9472;&#9472; ubuntu-server.seed
&#9492;&#9472;&#9472; README.diskdefines

73 directories, 177 files
```

---

### Post by oldfred on 2014-08-21
I have not tried with the newest server version, but never was able to get older server version to directly mount with grub2's loopback. 
The ISO does have to be configured for directly mounting I do not think they set up server version for that.

You have to dig into the syslinux boot files to find the paths and boot options that may apply. Do not know if grub can loopback an efi boot or not. And check that versions or extensions are the same.

The grub & loop files in the grub folder for efi boot may also show info on paths and common boot options.
In the isolinux folder are several linked text files for syslinux to boot. I trace down to text.cfg and it has the syslinux boot lines which show paths on one line and boot options on another.

---

### Post by pqwoerituytrueiwoq on 2014-10-24
answer:
```
    menuentry "Ubuntu Server 64bit" --class ubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/ubuntu-14.04.1-server-amd64.iso"
        loopback loop $isofile
        linux (loop)/install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet --
        initrd (loop)/install/initrd.gz

    }
```

---

### Post by oldfred on 2014-10-24
Good work pqwoerituytrueiwoq. :)

Also noted in your other thread that miniISO now works also.

---

### Post by yoniy0 on 2014-12-01
> **pqwoerituytrueiwoq said:**
> answer:
```
    menuentry "Ubuntu Server 64bit" --class ubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/ubuntu-14.04.1-server-amd64.iso"
        loopback loop $isofile
        linux (loop)/install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet --
        initrd (loop)/install/initrd.gz

    }
```
Actually, I find that this `menuentry` still results in the notorious "Incorrect CD-ROM detected" error in my setting (a pre-UEFI machine I'm trying to convert into a home server for 6-12 months). Perhaps someone else had the same problem but managed to solve it?

---

