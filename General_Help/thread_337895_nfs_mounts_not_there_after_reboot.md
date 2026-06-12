---
title: "nfs mounts not there after reboot"
date: 2007-01-13
forum: General Help
---

### Post by slickbob on 2007-01-13
Hi,

I just installed edgy and would like to mount all of my nfs shares from my server. I havn't had any trouble using SUSE in the past.  This is my first try @ ubuntu.

I edited my fstab file to add the mount points and I can mount them manually (using "mount /home/username/mountpoint"), but when I reboot my client machine the shares are no longer there. and I have to mount them manually again.

Here's a line from my /etc/fstab file:
192.168.1.1:/home/username        /home/username/mountpoint    nfs     rw,user     0       0

Any ideas why the /home/username/mountpoint isn't mounted when I reboot?

Thanks,
slick

---

### Post by Ramses de Norre on 2007-01-13
Are they mounted after you've explicitly done **sudo mount -a**?
Maybe you can explicitly add the "auto" option, although that should be the default..
You'll also want to add hard,intr options, they are safer and recommended on the official nfs site.

---

### Post by slickbob on 2007-01-13
They are there after I run "sudo mount -a".  Even when I add them in if I reboot, the shares still are not mounted.  Any more advice.
Thanks,
slick

---

