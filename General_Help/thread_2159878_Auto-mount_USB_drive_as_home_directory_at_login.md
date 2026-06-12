---
title: "Auto-mount USB drive as home directory at login?"
date: 2013-07-04
forum: General Help
---

### Post by zerubbabel on 2013-07-04
In our office we're setting up a computer lab with LTSP, with a thin client on each desk, and we'll have a couple of laptops for use by any of us when we have need to work out of the office. The laptops will be configured with the same software as is available on the lab server. What would be ideal is if each person could sync his home directory with a USB drive that could be plugged into the laptop before the user logs in on it, and upon login the file system on that USB drive would be mounted as the user's home directory on the laptop. Then when we get back to the office, we could just plug in the USB drive and re-sync with our home directory on the server. Is this feasible?

---

### Post by Cheesehead on 2013-07-04
Sure, but think about security and risk before you do that.
For example, it's a great way to introduce malware or older versions or mistaken-deletions from the USB into the server's home directory.

If you really want to do it, look at using an Upstart Job that runs at login and at USB insertion to unmount/remount the appropriate /home directory. [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/) can show you how.

---

### Post by zerubbabel on 2013-07-05
> **Cheesehead said:**
> Sure, but think about security and risk before you do that.
For example, it's a great way to introduce malware or older versions or mistaken-deletions from the USB into the server's home directory.


That could be prevented by choosing the rsync options carefully, to only copy modified or added files back to the home directory on the server, but not apply any deletions.

---

### Post by Cheesehead on 2013-07-06
Good thinking!

---

### Post by ben-Nabiy_Derush on 2013-08-01
What about an encrypted USB drive? We cannot get the thin client to send the info to the server, even though standard USB drives work.

---

