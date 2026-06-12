---
title: "virt-manager could not initialize SDL"
date: 2008-05-16
forum: General Help
---

### Post by jmandawg on 2008-05-16
I've installed virt-manager and libvirt and build kvm from source.  Everything works fine using vnc graphics display but when i try to switch to SDL i get the following error: 

```
     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-04-08 15:15)
(*) Direct/Memcpy: Using Generic 64bit memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
```

When i check the log file it is trying to run this command:
```

/usr/bin/kvm -M pc -m 512 -smp 1 -monitor pty -drive file=/root/Test.img,if=ide,boot=on -net nic,macaddr=00:16:3e:07:00:b4,vlan=0,model=virtio -net tap,fd=18,script=,vlan=0 -usb
```

When i run that command manually from the commandline it works fine and a qemu window opens. Why won't it run from virt-manager?

'/dev/fb0' and '/dev/fb/0' do not exist on my system, do i need to create them?

Thanks in advance.

-Jay

---

### Post by jmandawg on 2008-05-16
Nevermind, i restarted the libvirt service and now it's working...  You wouldn't believe how much time i wasted on that one.

---

### Post by rrwright on 2010-10-08
Thanks for your follow-up post! It probably saved me hours of trying to figure out the same problem. Easy solution. Thanks for the post.

---

