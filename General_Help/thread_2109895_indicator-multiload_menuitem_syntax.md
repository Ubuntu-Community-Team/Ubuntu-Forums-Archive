---
title: "indicator-multiload menuitem syntax"
date: 2013-01-28
forum: General Help
---

### Post by superglide03 on 2013-01-28
I'm a new member and relatively new to Linux.  I've never posted before so thank you for your efforts.
    The panel icon (in 12.10) dropdown menu for idicator-multiload (System Load Indicator version 0.3) shows a single cpu stat.  What I would like it to show is that same stat for all cpu's, as it does in system monitor.  Please see attached screenshot.  Also following each stat I would like the frequency posted. My efforts in this direction are on the menuitem for cpu4 (screenshot cursor location).
    I'm using the 3.7.0-030700-generic kernel if it matters.

Something like this would be nice.........   _Instead of what I have_...

    CPU1: 15% / 1.86 GHz......................................._CPU1: 15%_
    CPU2: 06% / 0.93 GHz
    CPU3: 21% / 2.26 GHz
    CPU4: 12% / 1.33 GHz
    
I hope I've supplied enough information and once again thank you.

---

### Post by mh21 on 2013-02-21
If you feel adventurous, you can try version 0.4 at ppa:indicator-multiload/daily. It doesn't give you frequency information yet, but it should allow you to do sth. like "CPU 1: $(percent(cpu.inuse0)), iowait $(percent(cpu.io0))", "CPU 2: $(percent(cpu.inuse1)), iowait $(percent(cpu.io1))" etc.

To get a list of allowed variables, use "indicator-multiload -l" on the command line.

Michael

---

### Post by superglide03 on 2013-02-27
Thank you Michael.  Your help was greatly appreciated.  It worked fantastically. I had given up on finding an answer.  Now I have four core reporting and once again thank you.

---

