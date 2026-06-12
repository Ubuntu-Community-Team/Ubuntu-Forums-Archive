---
title: "Maximum suspend/awakenings without restart?"
date: 2008-05-24
forum: General Help
---

### Post by Trevorius on 2008-05-24
I have the habit of going for long periods of time between restarts, preferring to put the system in suspend or standby (Windows) when not running. I do this for the sheer convenience of it, since it takes only a couple seconds to recover from suspend, even where there are numerous programs open snce I have 2 gigs of ram to work with.

However, last week when I tried to awaken the system, it aborted and when I started it again, it went into an fsck file system check which yeilded errors I had to manually correct. I wonder if since the ext2 partition was set to have a diagnostic every 38 mounts (I've since converted it to ext3), perhaps it refused mounting when coming out of suspend causing the failure.

I've heard of Linux systems running for long periods of time without restart, and I routinely went over a month on XP without consequence, but I wonder if that may not be healthful for my system - at least if I'm using hibernation/suspend. So what do you think? Is there a limit to how long I should go between restarts?

---

### Post by strabes on 2008-05-25
I don't believe that going for long periods of time without rebooting can actually do damage to your system. It will probably just start beginning to get slow. My parents (running ubuntu on their computer) used to go for >2-3 months without a reboot while I went away to college.

---

### Post by jpkotta on 2008-05-25
I generally do the same thing with my laptop, and I've never had trouble.  My understanding is that the filesystem is never unmounted/remounted during suspend/resume.

---

### Post by Trevorius on 2008-05-26
Thanks for the input guys, I feel much reassured.

---

