---
title: "Cover Art"
date: 2007-02-17
forum: General Help
---

### Post by energiya on 2007-02-17
Hi,
I just tried to install [albumart]("http://louhi.kempele.fi/~skyostil/projects/albumart/"), but when running as root
```

python setup.py install

```
I get
> 
Uic'in albumart_about_dialog_base.ui
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Uic'in albumart_configuration_dialog_base.ui
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Uic'in albumart_dialog_base.ui
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Uic'in albumart_exception_dialog_base.ui
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Uic'in albumart_string_list_widget_base.ui
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
running install
running build
running install_data
copying lib/albumart/albumart_about_dialog_base.py -> /usr/lib/albumart
copying lib/albumart/albumart_configuration_dialog_base.py -> /usr/lib/albumart
copying lib/albumart/albumart_dialog_base.py -> /usr/lib/albumart
copying lib/albumart/albumart_exception_dialog_base.py -> /usr/lib/albumart
copying lib/albumart/albumart_string_list_widget_base.py -> /usr/lib/albumart
running install_egg_info
Removing /usr/lib/python2.5/site-packages/albumart-1.6.0-py2.5.egg-info
Writing /usr/lib/python2.5/site-packages/albumart-1.6.0-py2.5.egg-info


and when running "albumart-qt"

> 
Traceback (most recent call last):
  File "/usr/bin/albumart-qt", line 145, in <module>
    sys.exit(runGui())
  File "/usr/bin/albumart-qt", line 77, in runGui
    import albumart_dialog
  File "/usr/lib/albumart/albumart_dialog.py", line 23, in <module>
    import Image
ImportError: No module named Image


Does anyone know what the problem is? And if not, what other programs can get album cover art for my music collection?

---

### Post by Titus A Duxass on 2007-02-17
Have you installed the other required packages?

I used apt-get to install these:

    *  Python 2.3 or better with python-xmlbase.
    * QT >= 2.3 or >= 3.1 and PyQT, the Python bindings.
    * Python Imaging Library
    * GNU make

On Debian the following command should get you rolling in a jiffy:

# apt-get install python-qt3 python-imaging

---

### Post by energiya on 2007-02-17
I had to install PyQT. Before that, I wasn't able to compile at all. So I get all the "nice" errors with all packages installed.

---

