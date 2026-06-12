---
title: "W: Possible missing firmware /lib/firmware/ast_dp501_fw.bin for module ast"
date: 2016-02-03
forum: General Help
---

### Post by wouter10 on 2016-02-03
I'm running Ubuntu 15.10 server on a Asrock E3C226D2I board. When I get a kernel update or run update-initramfs -u I get  a warning about missing firmware:

```
root@fileserver:~# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-4.2.0-27-generic
W: Possible missing firmware /lib/firmware/ast_dp501_fw.bin for module ast

```

I did some google-ing and found it might have something to do with DRM, I don't think I have any use for that since I'm running a server. Does anyone have an idea how to fix this?

---

