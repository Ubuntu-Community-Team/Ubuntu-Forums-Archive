---
title: "rsync -- &quot;Permission denied&quot;"
date: 2017-01-01
forum: General Help
---

### Post by JohnDillinger43 on 2017-01-01
I have an rsync script that runs nightly to back up critical files, and for some reason it's recently been unable to copy the files -- I get, for instance, "change_dir "/media/Pictures" failed: Permission denied (13)".  Add to that my discovery that it was never backing up some system files because of permissions issues, and I'd like to figure out the best way to get this working correctly.  I've seen a few different ideas tossed around, including adding the script to cron.daily or having the script run as su, so I wanted to get some feedback on best practices.  I'll note in advance that my Linux skills have degraded as I have to use Windows for work now, so I may have to ask some follow-up questions.  Thanks to all!

---

### Post by SeijiSensei on 2017-01-02
You need to run the script as root. The easiest way to do this is place it in /etc/cron.daily. Scripts in that directory run overnight as root.

---

