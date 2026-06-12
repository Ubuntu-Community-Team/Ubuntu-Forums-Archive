---
title: "Bootup Problem...Yikes!"
date: 2006-07-16
forum: General Help
---

### Post by kaje on 2006-07-16
I run Ubuntu 6.06 through Parallels. I haven't run the virtual machine in about 3 days (was working fine then) and went to boot it up and started getting these errors in this order:


[IMG]http://img.photobucket.com/albums/v57/kaje103/ubuntu/bootup2.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v57/kaje103/ubuntu/bootup3.jpg[/IMG]

---

### Post by FallenWizard on 2006-07-16
It looks like the hd is read-only. 


Look at: Engine lockfile... blabla... **READ ONLY FILESYSTEM**


Try to boot with a livecd and take the ro option out off fstab.

---

### Post by kaje on 2006-07-16
OK, I went into fstab and took out the "errors=remount-ro" after "defaults," under options for hda1 and I'm still getting the errors  in the pictures above.

---

