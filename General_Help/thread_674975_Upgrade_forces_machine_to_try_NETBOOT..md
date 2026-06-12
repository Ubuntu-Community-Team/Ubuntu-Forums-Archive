---
title: "Upgrade forces machine to try NETBOOT."
date: 2008-01-22
forum: General Help
---

### Post by flyinglizard on 2008-01-22
I have had Ubuntu 7.10 running since October.  This morning  I used the Update Manager to update to the latest fixes.

On the next reboot it displayed Grub,  then the Ubuntu splash screen then nothing.  I used Alt-F1 to display the terminal and it was looping looking for a NETBOOT server.  (This machine is my NETBOOT server)

Both the standard boot and the recovery boot attempted to NETBOOT.  This was using kernel 2.6.22.14

I then booted to an older kernel (2.6.22-12) from the Grub menu and got a successful boot (well LVM did not work but that is not an issue now.)

I poked around in /boot and used the bak version of initrd.img-2.6.22-14-generic,  I am now able to boot successfully to the 2.6.22-14 kernel.

So as of now all is well,  I am booting to 2.6.22-14 and everything works.  What information do I need to provide to debug the initial problem?

As a note this machine is a NETBOOT server for a diskless MythTV client,  could I have screwed this machine's configuration up when I went through the steps for the diskless machine?

John

---

