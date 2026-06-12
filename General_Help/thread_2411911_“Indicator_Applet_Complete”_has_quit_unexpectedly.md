---
title: "“Indicator Applet Complete” has quit unexpectedly"
date: 2019-02-05
forum: General Help
---

### Post by raleigh3 on 2019-02-05
This occurs every time I boot up.
  ```
  “Indicator Applet Complete” has quit unexpectedly

     If you reload a panel object, it will automatically be added back to the panel
```

I tried reinstalling the applet.

```
sudo apt purge indicator-applet-complete

sudo apt autoremove

sudo apt autoclean

sudo apt install indicator-applet-complete
```

---

### Post by #&amp;thj^% on 2019-02-05
This has been a long outstanding bug.:(....[https://ubuntu-mate.community/t/about-notification-area-and-indicator-applet-complete/16525/13](https://ubuntu-mate.community/t/about-notification-area-and-indicator-applet-complete/16525/13)
and: [https://bugs.launchpad.net/ubuntu-mate/+bug/1634682](https://bugs.launchpad.net/ubuntu-mate/+bug/1634682)
For myself i just open the terminal and run "killall mate-panel"
I have seen this issue moreover with an over crowded panel.

---

