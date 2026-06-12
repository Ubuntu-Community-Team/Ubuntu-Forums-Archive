---
title: "Error Booting Up Ubuntu"
date: 2012-11-07
forum: General Help
---

### Post by doggiedog1 on 2012-11-07
Whenever I try to boot into Ubuntu from the GRUB menu an error message pops up:

[FONT="Courier New"][INDENT]mountall: /lib/x86_64-linux-gnu/libc.so.6:version'GLIBC_2.14' not found (required by /lib/libply.so.2)
General error mounting filesystems
A maintenance shell will now be started
CONTROL-D will terminate this shell and reboot the system.
Five root password for maintenance (or type CONTROL-D to continue):[/INDENT][/FONT]

I'm not sure how to go about fixing this or what had happened. I believe that I was updating to the newest version, but my computer died during it (I had to leave it running and my roommate apparently unplugged my charger).

---

### Post by Rubi1200 on 2012-11-10
Hi and welcome to the forums :-)

I suggest using a LiveCD/USB to try and boot the computer.

Then follow the instructions in the link at the bottom of my post and run the boot info script.

Post the results of the file here and we can try and assist you further.

Thanks.

---

### Post by grahammechanical on 2012-11-10
> my computer died during it (I had to leave it running and my roommate apparently unplugged my charger).

You have a broken operating system. The Grub menu seems to be doing its stuff but the operating system cannot load because there are missing libraries.

The upgrade process has to use the existing libraries to download all the new stuff, then at some point it has to disconnect the old stuff and initiate the new stuff all the time while keeping the operating system working. A reboot brings up the new operating system.

This process was interrupted and now the OS cannot be booted. You best bet is to use the Live DVD to save your data and reinstall.

This is my opinion. It is most likely the quickest and easiest way of getting back a working system.

Regards.

---

### Post by HiImTye on 2012-11-10
I would boot a liveCD and check /var/log/apt/kern.log to see what packages were upgraded. you should be able to reinstall them using the liveCD

unless of course you were upgrading from one version of ubuntu to another version of ubuntu. in that case, a fresh install is probably in order

---

