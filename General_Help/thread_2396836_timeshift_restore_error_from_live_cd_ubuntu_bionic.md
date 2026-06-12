---
title: "timeshift restore error from live cd ubuntu bionic"
date: 2018-07-21
forum: General Help
---

### Post by Seadevil on 2018-07-21
need help. can't boot up ubuntu. get error msg:  216065][drm:radeo_vga_detect[radeon]]*ERROR*vga-1:Probed a monitor but no| invalid EDID
did a filecheck with gparted , got red flags on these:  jfsutils ntfsprogs reiser4progs reiserfsprogs xfsprogs.....so I tried to reboot again and
with ubuntu recovery.....
on the black screen everything was " [OK]  until it got to :  started kupdate UTMP about System Runlevel Changes-
and it hangs there forever......

so I thought it would be easier to run a live cd and run timeshift --recover.    NOW i get these errors:


[HTML]E: Error creating directory /mnt/timeshift: Permission denied
E: Failed to create directory: /mnt/timeshift/restore
E: Error creating directory /mnt/timeshift: Permission denied
E: Failed to create directory: /mnt/timeshift/restore/
E: Failed to mount device '/dev/sda7' at mount point '/mnt/timeshift/restore/'
E: mount: only root can do that

[/HTML

can anyone help?  or do i have to re-install ubuntu and run timeshare from inside there?  or can i somehow get permissions from the live cd ?

ok, no answers....so i just RE-INSTALLED ubuntu & restored with timeshift and  back in time.  took an hour or so, but got it done.

---

