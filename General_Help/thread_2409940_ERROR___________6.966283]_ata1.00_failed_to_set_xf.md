---
title: "ERROR           6.966283] ata1.00: failed to set xfermode (err_mask=0x40)"
date: 2019-01-08
forum: General Help
---

### Post by tinny123 on 2019-01-08
6.966283] ata1.00: failed to set xfermode (err_mask=0x40)

Hello
I'm getting this message and a slow boot on ubuntu 18.04 with kernel   4.20. however this does not occur when i use kernel 4.15. any kernel   after that gives me this message during bootup. Any advice on how to fix   please?

kubuntu 18.04 , dell latitude e6430

---

### Post by dbergst on 2019-01-09
I saw this solution to issues similar to yours during an Internet search.  If you make the following update to /etc/default/grub, then run sudo update-grub, see if it helps.

GRUB_CMDLINE_LINUX_DEFAULT = "libata.force = noncq"

---

### Post by tinny123 on 2019-01-11
the issue stays the same . just a lot of text appears during boot.  I was advised over at kubuntu forums to avoid updating to mainline kernel and stick to what ships with  my distro as the distro developers ( ubuntu and kde etc) add a lot of patches etc. so apparently the 4.16 onwards kernels are not supported as yet.

Also could you please tell me what the command you told me does in detail? Im a noob

---

