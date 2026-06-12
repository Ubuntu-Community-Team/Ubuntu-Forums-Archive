---
title: "House keeping question"
date: 2006-08-07
forum: General Help
---

### Post by l.j. on 2006-08-07
Loving Ubuntu total linux convert lol had to say that, any how is thier a way to check for fragmented files or temp files that can be deleted still learning the file system i know in windows sometimes thiers left over fragments tmps etc just curious if thats the case here thanx in advance :)

---

### Post by scxtt on 2006-08-07
there is a /tmp folder ... but you shouldn't have to worry about fragmentation, and running a fsck (when the drive is unmounted! [do a **shutdown -F -r now** to get started]) should help w/ any filesystem errors ...

other than that, if you're looking to save space - you can run **sudo apt-get clean** to clear out the repo cache (.debs you don't necessarily need anymore) ...

---

### Post by l.j. on 2006-08-07
:D Thanx for the advice greatly appreciated.

---

### Post by -deadcats on 2006-08-07
WackToMack has a great HOWTO here for cleaning up stuff: [http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

CRON also takes care of a lot of the mundane tasks. Other than that, you're pretty much set.

Most Windows users go through a bit of a shock when they find out that Linux doesn't require the heavy maintenance that Windows does. That's cool. :)

regards,
-dc

---

