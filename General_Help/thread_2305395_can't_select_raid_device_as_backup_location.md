---
title: "can't select raid device as backup location"
date: 2015-12-05
forum: General Help
---

### Post by silverspr on 2015-12-05
HI, not sure how to post this:
Both timeshift and redo clone will not allow a raid device as a backup location.  Does this sound right?  I've rebuilt my raid array thinking it might have not been properly configured.  Didn't resolve, but I can chose any other device i.e. /dev/sda1 but not the /dev/md0.  Using wily, mdadm on 2 TB drives configured as raid 1 partitioned as two arrays RD1 and RD2.

thanks

---

### Post by silverspr on 2015-12-07
HI, the only way I could resolve this was to uninstall mdadm and turn on 'fakeraid'. Now I can select the raid device i.e. dm-1 or dm-2 as a backup location with either Timshift or doclone. Not sure if this is a shortcoming of the application or the operating system or mdadm. I would have preferred to stay with mdadm as I've read it is more robust than dmraid, but not if I am not able to select a raid device as my backup location.

thanks, if there is some other way of doing this to get the outcome I want, I'm all ears.

---

