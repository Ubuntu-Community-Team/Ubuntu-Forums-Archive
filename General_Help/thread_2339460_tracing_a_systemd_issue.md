---
title: "tracing a systemd issue"
date: 2016-10-09
forum: General Help
---

### Post by Andrew_Welham on 2016-10-09
I keep seeing the following in the syslog. When this error shows serviio media player stops, but nothing appears in the serviio logs, even when serviio works again, so i suspect maybe its just paused. Not sure what else happens.
I have also noticed this error when serviio is not being used i.e at 3am in the morning.
How can i trace what is upsetting systemd, as it may be nothing to do with serviio, but its the only effect i can see. Also this can't be triggered and happens every few weeks

Oct  8 20:29:14 digitalpower systemd[1]: Created slice User Slice of andrew.
Oct  8 20:29:14 digitalpower systemd[1]: Starting User Manager for UID 1000...
Oct  8 20:29:14 digitalpower systemd[1]: Started Session 1476 of user andrew.
Oct  8 20:29:14 digitalpower systemd[18692]: Reached target Sockets.
Oct  8 20:29:14 digitalpower systemd[18692]: Reached target Timers.
Oct  8 20:29:14 digitalpower systemd[18692]: Reached target Paths.
Oct  8 20:29:14 digitalpower systemd[18692]: Reached target Basic System.
Oct  8 20:29:14 digitalpower systemd[18692]: Reached target Default.
Oct  8 20:29:14 digitalpower systemd[18692]: Startup finished in 55ms.
Oct  8 20:29:14 digitalpower systemd[1]: Started User Manager for UID 1000.
Oct  8 20:34:41 digitalpower systemd[1]: Stopping User Manager for UID 1000...
Oct  8 20:34:41 digitalpower systemd[18692]: Stopped target Default.
Oct  8 20:34:41 digitalpower systemd[18692]: Reached target Shutdown.
Oct  8 20:34:41 digitalpower systemd[18692]: Starting Exit the Session...
Oct  8 20:34:41 digitalpower systemd[18692]: Stopped target Basic System.
Oct  8 20:34:41 digitalpower systemd[18692]: Stopped target Sockets.
Oct  8 20:34:41 digitalpower systemd[18692]: Stopped target Timers.
Oct  8 20:34:41 digitalpower systemd[18692]: Stopped target Paths.
Oct  8 20:34:41 digitalpower systemd[18692]: Received SIGRTMIN+24 from PID 19359 (kill).
Oct  8 20:34:41 digitalpower systemd[1]: Stopped User Manager for UID 1000.
Oct  8 20:34:41 digitalpower systemd[1]: Removed slice User Slice of andrew.
Oct  8 20:35:11 digitalpower systemd[1]: Created slice User Slice of andrew.
Oct  8 20:35:11 digitalpower systemd[1]: Starting User Manager for UID 1000...
Oct  8 20:35:11 digitalpower systemd[1]: Started Session 1482 of user andrew.
Oct  8 20:35:11 digitalpower systemd[29802]: Reached target Timers.
Oct  8 20:35:11 digitalpower systemd[29802]: Reached target Paths.
Oct  8 20:35:11 digitalpower systemd[29802]: Reached target Sockets.
Oct  8 20:35:11 digitalpower systemd[29802]: Reached target Basic System.
Oct  8 20:35:11 digitalpower systemd[29802]: Reached target Default.
Oct  8 20:35:11 digitalpower systemd[29802]: Startup finished in 29ms.
Oct  8 20:35:11 digitalpower systemd[1]: Started User Manager for UID 1000.
Oct  8 20:36:21 digitalpower systemd[1]: Stopping User Manager for UID 1000...
Oct  8 20:36:21 digitalpower systemd[29802]: Stopped target Default.
Oct  8 20:36:21 digitalpower systemd[29802]: Stopped target Basic System.
Oct  8 20:36:21 digitalpower systemd[29802]: Stopped target Paths.
Oct  8 20:36:21 digitalpower systemd[29802]: Reached target Shutdown.
Oct  8 20:36:21 digitalpower systemd[29802]: Starting Exit the Session...
Oct  8 20:36:21 digitalpower systemd[29802]: Stopped target Sockets.
Oct  8 20:36:21 digitalpower systemd[29802]: Stopped target Timers.
Oct  8 20:36:21 digitalpower systemd[29802]: Received SIGRTMIN+24 from PID 19733 (kill).
Oct  8 20:36:21 digitalpower systemd[1]: Stopped User Manager for UID 1000.
Oct  8 20:36:21 digitalpower systemd[1]: Removed slice User Slice of andrew.

---

