---
title: "Software center broken after upgrading from 12.10"
date: 2013-04-29
forum: General Help
---

### Post by r0h1 on 2013-04-29
Hi all,
I updated ubuntu to latest version, and now the ubuntu software center is not working any more. I click to open it, it seems it "loads" (the icon on the left vertical bar is flashing), and then... nothing, no window will open, not even an error or bug report window. 
I tried uninstalling via terminal, also using the -purge option, and reinstall it, restarting the pc, but nothing has changed.
I checked in the .config folder, there's no software-center folder in it.

I use my laptop, a DELL Latitude e5420 (intel i5, 4gb ram, intel hd3000)

Thanks a lot for all your help!

---

### Post by ibjsb4 on 2013-04-29
Open it in terminal and see what errors you get.

```
software-center
```

---

### Post by r0h1 on 2013-04-29
Thanks

```

Traceback (most recent call last):
  File "/usr/bin/software-center", line 128, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 37, in <module>
    import webbrowser
  File "/usr/lib/python2.7/webbrowser.py", line 505, in <module>
    register_X_browsers()
  File "/usr/lib/python2.7/webbrowser.py", line 489, in register_X_browsers
    register(browser, None, Chrome(browser))
NameError: global name 'Chrome' is not defined

```

some issue with chrome?

---

### Post by r0h1 on 2013-04-29
In fact I uninstalled chrome, and the software center works again... but if I reinstall it (from the .deb package on google chrome site) the software center is again broken :\

---

### Post by ibjsb4 on 2013-04-29
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=NameError%3A+global+name+%27Chrome%27+is+not+defined&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=NameError%3A+global+name+%27Chrome%27+is+not+defined&sa=Search&cof=FORID:9)

---

