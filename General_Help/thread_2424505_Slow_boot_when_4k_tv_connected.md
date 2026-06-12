---
title: "Slow boot when 4k tv connected"
date: 2019-08-09
forum: General Help
---

### Post by bjlockie on 2019-08-09
The task bar is really slow to show when my 4k tv is connected.
I think the desktop comes up in the same amount of time.
It is fast when the hdmi to the tv is unplugged.

I did systemd-analyze blame before and after and it seems to be alsa-restore.service
no_tv: 77ms alsa-restore.service
with_tv: 13.110s alsa-restore.service
with_tv (2nd run): 14.269s alsa-restore.service

The full systemd-analyze output is here:
[http://lockie.ca/test/systemd-analyze-blame_no_tv.txt](http://lockie.ca/test/systemd-analyze-blame_no_tv.txt)
[http://lockie.ca/test/systemd-analyze-blame_with_tv.txt](http://lockie.ca/test/systemd-analyze-blame_with_tv.txt)
[http://lockie.ca/test/systemd-analyze-blame_with_tv2.txt](http://lockie.ca/test/systemd-analyze-blame_with_tv2.txt)

---

### Post by bjlockie on 2019-08-10
Very weird, I turned on fast boot and it is fast for the desktop to come up.
Loading the taskmanager panel is really slow (only with the 4k tv connected so maybe is has to do with the large desktop resolution).

---

