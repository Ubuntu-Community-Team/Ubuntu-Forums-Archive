---
title: "[SOLVED] Grub error 17 and data recovery"
date: 2008-05-20
forum: General Help
---

### Post by Goldpin on 2008-05-20
I had a disk crash, and was getting Grub error 17.  I have managed to recover most of the data and reinstall Grub.  My Ubuntu drive (hdb) will now mount and I can see it when I'm using the Ubuntu live CD.  However, when I try to boot into Ubuntu from the hard drive Ubuntu will begin to load and then freeze.  When I try to boot up using the recovery mode, I get the following messages:

kernel panic - not syncing attempting to kill ima (or something similar)
run-init:  /sbin/init no such file or directory.

Also see ATKBD.C spurious ACK on ISU 00601serio0 some program might be trying to access hardware directly.

There are a lot of files in my lost+found directory which seem to be broken. Is there any way to recover them?

I've looked for /sbin/init and it is there, are there any other files that should be there?  If so, how can I replace them?

I'd like to copy my home folder to another drive, but the live CD says I don't have the permissions to do it.  Should I try to do that from a terminal using sudo?  If so, what would the syntax be?

Thanks in advance.

---

### Post by ryanhaigh on 2008-05-20
From the livecd you can open the filebrowser as root using alt-f2 to bring up the run dialog and enter gksudo nautilus, you should then be able to copy the files from your home folder. If your home folder is on the same partition as the lost+found folder with all the files I would also recommend grabbing those. These are files that are recovered during a disk check so they may be important to you. 

I wouldn't be terribly concerned with getting your system booting again just try and get your important data.

---

