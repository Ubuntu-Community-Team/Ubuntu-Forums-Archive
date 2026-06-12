---
title: "iscsi support in Ubuntu 8"
date: 2008-04-28
forum: General Help
---

### Post by aspasiasf on 2008-04-28
Hello

The readme states that iscsi support is included in the latest Ubuntu release and should be in place when the argument: "iscsi=true" is passed to the kernel during installation.

My question:  If I did not do the above; what are the steps or instructions to enable iscsi support POST-installation?

Any help would be greatly appreciated.

regards,

Aspasia.

---

### Post by laniohma on 2008-04-28
I have this same question.  

I have a number of 7.0.4 server boxes which I want to perform a network upgrade.

I am looking for documentation on using "iscsi=true" during the network upgrade to enable the feature in my upgraded hosts.  

Also I do require a network upgrade as the graphical environment is not desireable for my hosts.

I cannot locate much documentation on the new server version except the upgrade paths.

Any help is appreciated.


It would be awesome if the doco was available & showed how to do both targets & initiators with server 8.0.4

---

### Post by aspasiasf on 2008-04-28
Update:
-------

So I installed a second box, and passed the iscsi=true parameter before the installation; and I am not sure what the difference is?

I went ahead and configured:
- install iscsi initiator utilities
- fdisk'ed and mk2fs'ed the device - /dev/sde1 in my case
- mount /dev/sde1 /mnt/iscsi
- tar'ed over my root FS into the /mnt/iscsi device ...
- edit the /mnt/iscsi/etc/fstab to reflect the new iscsi root 

My question is:  in the Centos and Fedora distros, at this point, it i just re-run the mkinitrd and pass the option pointing to /mnt/iscsi/etc/fstab - the initrd they generate already loads and copies the modules required for booting and it also automatically created the iscsistart command.

Is there a similar process here in Ubuntu?  Better yet, is there a documentation that outlines how to prepare an Ubuntu root disk image for diskless servers booting over iscsi root?

thanks again.

Aspasia.

---

