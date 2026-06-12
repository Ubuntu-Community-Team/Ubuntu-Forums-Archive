---
title: "gutsy + upstart continues booting past interactive scripts"
date: 2007-10-25
forum: General Help
---

### Post by vom on 2007-10-25
I have a  pretty simple script that runs at boot time.  It lives in /etc/init.d, I've added it with update-rc.d etc.  Script exits 0 cleanly etc.  Worked fine in Feisty.  By worked fine, I mean that my "read VAR" actually made the graphical boot process give way to text mode and let me answer the script's questions.  In Gutsy, this does not happen :(

What is happening now in Gutsy is that the script it sitting there waiting for input that it won't ever get.  I can see it in ps, see that rc2 is waiting from initctl list etc.

Is this an upstart thing ?  I never even noticed if Feisty was using upstart or not, but it looks like Gutsy is.

What do I have to do to make this script 'stop the presses' and not have upstart keep rolling ?  Thanks.

---

