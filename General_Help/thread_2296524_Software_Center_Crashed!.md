---
title: "Software Center Crashed!"
date: 2015-09-26
forum: General Help
---

### Post by melvin15 on 2015-09-26
Hi, 

I did check the forum for Software Center not working. However, I think I have narrowed down to whats causing my issue and it look different to me. 

Tried running software center from the console and I have this error. This was after repeated remove/autoremove/purge etc. 

> 2015-09-26 19:54:28,980 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 407, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/historypane.py", line 79, in __init__
    self._get_emblems(self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/historypane.py", line 199, in _get_emblems
    pb = icons.load_icon(emblem, self.ICON_SIZE, 0)
gi._glib.GError: Error opening file: No such file or directory

I did try out commenting the lines in there but it then errors out the calling function and I can´t figure out the data flow. It does seem to me that **self.icon** properties are the one that is corrupted. 

Any solutions please

---

### Post by v3.xx on 2015-09-26
The forum has many post on this

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Software+Center+Crash&as_qdr=all&sa=Google+Search&lang=en&siteurl=](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Software+Center+Crash&as_qdr=all&sa=Google+Search&lang=en&siteurl=)

I think the bottom line is this

[http://www.datamation.com/open-source/the-death-of-ubuntus-software-center.html](http://www.datamation.com/open-source/the-death-of-ubuntus-software-center.html)

I use Synaptic Package Manager

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

I have tried 'app grid' and found it blazing fast, but did no further testing on it as I am happy with SPM.

If you wish to continue trouble shooting USC, you may find some ideas here.

[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by melvin15 on 2015-09-27
the bottom line really got me upto speed. And I think I going to keep using SPM !!

THANK YOU!! :)

---

### Post by v3.xx on 2015-09-28
Welcome To the forums :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

