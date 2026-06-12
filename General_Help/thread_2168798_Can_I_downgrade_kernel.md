---
title: "Can I downgrade kernel?"
date: 2013-08-19
forum: General Help
---

### Post by Lateralus138 on 2013-08-19
Hello all I have recently (and finally) successfully upgraded to 13.04 and for a while now (in 12.10 as well) I have had problems with wireless not connecting. After a lot of searching asking for help in forums with no working solution I went to the Realtek site and found that my wireless card driver only supports up to 3.2x kernels. I have emailed them asking if they are working on an updated version, but waiting on a reply. I was wondering if it is possibly to downgrade my kernel and if it will work then or if other things might break if I do so. 

Running:

OS = Ubuntu 13.04 64 bit

Laptop = Toshiba Satellite SE M505-S4940

Wireless =  Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)

---

### Post by A Bunny on 2013-08-19
Yes I think you can see link
[http://ubuntuforums.org/showthread.php?t=1871136](http://ubuntuforums.org/showthread.php?t=1871136)

Hope this helps.

---

### Post by Lateralus138 on 2013-08-19
> **A Bunny said:**
> Yes I think you can see link
[http://ubuntuforums.org/showthread.php?t=1871136](http://ubuntuforums.org/showthread.php?t=1871136)

Hope this helps.

Thanks, that was sort of helpful, but the 3.2 kernel isn't in the repositories and I had trouble finding it. I did find a working solution to install it though. All packages seem to work fine with the exception of the virtual package for VMs which really doesn't matter, but it's just missing dependencies. Check the link below for the solution I found:
[http://linuxg.net/how-to-install-linux-kernel-3-2-47-lts-on-ubuntu-13-10-13-04-12-10-12-04-and-linux-mint-15-14-13-via-installation-script/#comment-48757](http://linuxg.net/how-to-install-linux-kernel-3-2-47-lts-on-ubuntu-13-10-13-04-12-10-12-04-and-linux-mint-15-14-13-via-installation-script/#comment-48757)

---

