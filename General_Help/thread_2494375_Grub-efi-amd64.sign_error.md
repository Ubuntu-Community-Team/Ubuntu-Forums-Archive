---
title: "Grub-efi-amd64.sign error"
date: 2024-01-14
forum: General Help
---

### Post by mrivner1 on 2024-01-14
I am getting grub errors when I run the apt -get command.  I am running Ubuntu 22.04.3 on an AMD server.  I do not get this error when running Ubuntu 22.04.3 on an Intel server with the same setup otherwise.

This is a sample of the error.

Installing package(s) with command apt-get -y install libsqlite3-0 openssh-client openssh-server openssh-sftp-server..
Setting up grub-efi-amd64-signed (1.187.6+2.06-2ubuntu14.4) ...
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.
dpkg: error processing package grub-efi-amd64-signed (--configure):
installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
grub-efi-amd64-signed

The script then goes on to install the updates requested and I have not seen any malfunctions from this error.  However, I would like not to see this error message.  I have been getting this message for several months every time I run the apt -get command.  But as far as I can tell all the upgrades have updated sucessfully.

I hope someone has a solution to this problem.

Thanks,
Michael

---

