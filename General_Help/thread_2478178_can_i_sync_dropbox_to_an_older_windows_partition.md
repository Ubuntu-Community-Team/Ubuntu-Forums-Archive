---
title: "can i sync dropbox to an older windows partition"
date: 2022-08-18
forum: General Help
---

### Post by artificialname on 2022-08-18
I have a desktop PC with a large amount of dropbox files synced to it

i just installed ubuntu on that PC, on a 100gb partition, and left the old windows partition (1800gb) untouched. 

From ubuntu, i am able to double click the  windows partition and view all my drop box files synced there.

I have downloaded dropbox to ubuntu but when i try to click "move" in drop box settings, to link it to the already synced files on the windows partition, i get an error message "you can't link dropbox to this location"

is there anyway I can link dropbox to that location?

Thanks!

---

### Post by QIII on 2022-08-18
Is the "old Windows partition" still bootable?  Was it completely unmounted the last time Windows was shut down?  For many years, Windows has used some subterfuge, with the help of hardware manufacturers, to make it appear to start up more quickly:  it enters a hybrid hibernation condition.  It does not cleanly unmount partitions to do so.

Linux distributions will not change the state of such not-quite-fully-unmounted Windows partitions.  The reason for that is to avoid causing reboot issues with Windows because the state of the disk has changed.

You can view the files in "read-only" mode just as always, but you cannot change/save/delete/add files on the partition.

Can you boot to the Windows partition?  If so, someone can help you learn to do a full shutdown.

---

### Post by artificialname on 2022-08-18
Thanks!
Yes it is s till bootable. How do i do a full shutdown and unmount?

---

