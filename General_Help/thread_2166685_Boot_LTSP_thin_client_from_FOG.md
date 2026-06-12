---
title: "Boot LTSP thin client from FOG"
date: 2013-08-10
forum: General Help
---

### Post by darkapec on 2013-08-10
I have made a post on the FOG forums, but this community is much more active. I am trying to have LTSP and FOG on the same server. Ideally the server would gPXE boot to FOG and then there would be an entry to boot the thin client environment. 

I currently have the following FOG config:

```


LABEL Ubuntu LTSP 12.04

        MENU LABEL LTSP - Ubuntu Desktop

        KERNEL linux.c32
         append tftp:/192.168.1.145/opt/ltsp/i386/boot/vmlinuz  initrd=tftp:/192.168.1.145/opt/ltsp/images/i386.img ro quiet splash

```

As you can see it is trying to grab the files from /opt/ltsp. This resulted in "tftp:/192.168.1.145/opt/ltsp/i386/boot/vmlinuz" file  not found. So I thought FOG could not see any files or folders outside of the /tftpboot/ directory. I then created a loopback mount and mounted /opt/ltsp on /tftpboot/ltsp. Then changed the FOG config to:


```


LABEL Ubuntu LTSP 12.04

        MENU LABEL LTSP - Ubuntu Desktop
        KERNEL linux.c32
         append tftp:/192.168.1.145/ltsp/i386/boot/vmlinuz  initrd=tftp:/192.168.1.145/ltsp/images/i386.img ro quiet splash


```
I am still getting the same error, "tftp:/192.168.1.145/ltsp/i386/boot/vmlinuz" file  not found. Should I try and set this up through apache and use HTTP:// instead of tftp:/? 



Has anyone been successful with this in  the past? Or is there anyway to verify FOG is able to see the directory  I am trying load the image from?

Thanks

---

### Post by darkapec on 2013-08-10
I have got a little further, using the following;

```

LABEL Ubuntu LTSP 12.04
        MENU LABEL LTSP - Ubuntu Desktop
        KERNEL ltsp/i386/boot/linux.c32
        APPEND ltsp/i386/boot/vmlinuz initrd=ltsp/i386/boot/initrd.img ro quiet splash

```

This boots to a busybox shell. When I attempt to exit the shell it kernel panics... but I am making headway.

---

