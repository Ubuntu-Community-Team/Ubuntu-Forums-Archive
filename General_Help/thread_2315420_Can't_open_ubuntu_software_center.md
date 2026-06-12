---
title: "Can't open ubuntu software center"
date: 2016-02-28
forum: General Help
---

### Post by andrey39 on 2016-02-28
Can't open ubuntu software center.
when i type in terminal software-center...
here the output:

```
ERROR:root:DebFileApplication import
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
    from debfile import DebFileApplication, DebFileOpenError
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
    from softwarecenter.db.application import Application, AppDetails
  File "/usr/share/software-center/softwarecenter/db/application.py", line 28, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 199, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 174, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named kali
Traceback (most recent call last):
  File "/usr/bin/software-center", line 128, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 54, in <module>
    from softwarecenter.db.application import Application
  File "/usr/share/software-center/softwarecenter/db/application.py", line 28, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 199, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 174, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named kali


```

---

### Post by coldraven on 2016-02-29
What version of Ubuntu are you using and why do want to run the software centre from a terminal?

---

### Post by X-RED_Tech on 2016-02-29
> **coldraven said:**
> What version of Ubuntu are you using and why do want to run the software centre from a terminal?

The message suggests Kali:
```
[COLOR=#000000][FONT=Ubuntu Mono]ImportError: No module named kali[/FONT][/COLOR]
```

Does Kali support USC? I don't really know the distro. Heard something about it, that's all.

---

### Post by andrey39 on 2016-02-29
> **coldraven said:**
> What version of Ubuntu are you using and why  do want to run the software centre from a terminal?

ubuntu 15.10 64-bit .
i did run it from the terminal because this way you can see the reason why it does not work..
the termina shows the errors that are behind the scenes...

---

### Post by coldraven on 2016-03-01
On 15.10 64 bit I get a couple of warnings but the Software centre does work. Maybe you need to purge it and re-install or just use Synaptic instead.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

```
~$ software-center
2016-03-01 08:01:26,948 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
2016-03-01 08:01:27,179 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2016-03-01 08:01:29,744 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2016-03-01 08:01:30,718 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2016-03-01 08:01:30,764 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2016-03-01 08:01:30,901 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
/usr/bin/software-center:184: Warning: Source ID 78 was not found when attempting to remove it
  Gtk.main()
/usr/bin/software-center:184: Warning: Source ID 153 was not found when attempting to remove it
  Gtk.main()
2016-03-01 08:01:41,351 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0


```

---

### Post by vasa1 on 2016-03-01
> **X-RED_Tech said:**
> The message suggests Kali: ...
Does Kali support USC? I don't really know the distro. Heard something about it, that's all.
Good catch. I suppose Kali has its own support forum which would be the more logical place to seek an fix.

---

### Post by andrey39 on 2016-03-13
i dont use with kali linux....

---

