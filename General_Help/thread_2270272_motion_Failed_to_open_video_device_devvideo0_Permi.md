---
title: "motion: Failed to open video device /dev/video0: Permission denied"
date: 2015-03-21
forum: General Help
---

### Post by r.stiltskin on 2015-03-21
I'm experiencing this permissions problem on a remote machine running Xubuntu 14.04 (with a Logitech usb webcam).  I (as ordinary user) can't get motion to open the video stream, but when I run sudo motion it works correctly and captures snapshots as I have configured in ~/.motion/motion.conf.

On my local desktop, also running Xubuntu 14.04 with a Logitech usb webcam, my ordinary user can run motion and it accesses /dev/video0 OK.

The ordinary user accounts on the 2 machines are identical -- same group memberships.  Also, the "motion" user accounts on both machines are the same -- both belong to groups motion and video.  And ~/.motion/motion.conf is the same on both machines.

Also, I can ssh in from my laptop to the local desktop and run motion as ordinary user.  But if i ssh from the laptop to the remote desktop motion only works with sudo.

So I don't think this is a motion problem, or a luvc problem.  Maybe something related to pam or ssh, but don't know where to look.  Any ideas?

---

### Post by dieter-erich on 2015-06-08
Hi,
    sorry for not being able to help, but I am having a similar issue: motion seems to start correctly (without error message) but I do not get any video stream: In the browser it shows a grey image with the text: "Unable to open video device since (a date)". However, the video device can be opened in cheese and camorama. So, what? Thanks for hints, D-E

---

