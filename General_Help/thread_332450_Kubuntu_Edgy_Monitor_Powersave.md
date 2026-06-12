---
title: "Kubuntu Edgy Monitor Powersave"
date: 2007-01-06
forum: General Help
---

### Post by dtruesdale on 2007-01-06
Everytime I restart the X session it resets the time for powersave for the monitor to 5 hours. Is there some place I can set this since it will not keep it any other way.

---

### Post by der_joachim on 2007-01-06
You can save your preferred settings in your xorg.conf. 

Add the following lines in your ServerLayout section:
```

Option         "BlankTime" "10"
Option         "StandbyTime" "30"
Option         "OffTime" "60"

```

This will blank your monitor after 10 minutes, it will go standby after 30 and after a full hour it'll switch itself off.

---

### Post by Moloko on 2007-02-03
I tried to solved this problem like der_joachim explain, It worked for me when I was using Kubuntu 6.06, but, I don't know why, with Edgy doesn't work.

Finally solved this problem updating KDE to the version 3.5.6.

[http://kubuntu.org/announcements/kde-356.php](http://kubuntu.org/announcements/kde-356.php)

Now works fine.

---

