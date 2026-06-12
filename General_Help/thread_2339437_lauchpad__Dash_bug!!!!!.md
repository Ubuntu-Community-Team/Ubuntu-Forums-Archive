---
title: "lauchpad / Dash bug!!!!!"
date: 2016-10-08
forum: General Help
---

### Post by 243750496 on 2016-10-08
1st why the software kazam and tickeys installed but show up such things ,2nd why remove them all shown not installed and the icons there and simple backup can run(checked ./local/share/applications no that software both /usr/share/applications) is it a bug?how to slove that?mostly all postings on web all with wine applications,btw i am using Ubuntu 16.04

```
cc@CC:~$ kazam
/usr/local/bin/kazam:32: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
Traceback (most recent call last):
  File "/usr/local/bin/kazam", line 146, in <module>
    from kazam.app import KazamApp
  File "/usr/local/lib/python3.5/dist-packages/kazam/app.py", line 35, in <module>
    from kazam.backend.prefs import *
  File "/usr/local/lib/python3.5/dist-packages/kazam/backend/prefs.py", line 478, in <module>
    prefs = Prefs()
  File "/usr/local/lib/python3.5/dist-packages/kazam/backend/prefs.py", line 121, in __init__
    self.read_config()
  File "/usr/local/lib/python3.5/dist-packages/kazam/backend/prefs.py", line 199, in read_config
    self.audio_source = int(self.config.get("main", "audio_source"))
  File "/usr/local/lib/python3.5/dist-packages/kazam/backend/config.py", line 103, in get
    return ConfigParser.get(self, section, key)
  File "/usr/lib/python3.5/configparser.py", line 797, in get
    d)
  File "/usr/lib/python3.5/configparser.py", line 393, in before_get
    self._interpolate_some(parser, option, L, value, section, defaults, 1)
  File "/usr/lib/python3.5/configparser.py", line 406, in _interpolate_some
    rawval = parser.get(section, option, raw=True, fallback=rest)
TypeError: get() got an unexpected keyword argument 'raw'

cc@CC:~$ tickeys
[Errno 2] No such file or directory: '/home/cc/.tickeys/tickeys_GUI_window_id'
System checking...
System checking success. Your system is supported
[INFO   ] [Logger      ] Record log in /home/cc/.kivy/logs/kivy_16-10-09_0.txt
[INFO   ] [Kivy        ] v1.9.0
[INFO   ] [Python      ] v2.7.12 (default, Jul  1 2016, 15:12:24) 
[GCC 5.4.0 20160609]
[INFO   ] [Factory     ] 173 symbols loaded
[INFO   ] [Image       ] Providers: img_tex, img_dds, img_gif, img_sdl2 (img_pil, img_ffpyplayer ignored)
[INFO   ] [Text        ] Provider: sdl2
[INFO   ] [OSC         ] using <multiprocessing> for socket
[INFO   ] [Window      ] Provider: sdl2(['window_egl_rpi'] ignored)
[INFO   ] [GL          ] OpenGL version <3.0 Mesa 11.2.0>
[INFO   ] [GL          ] OpenGL vendor <Intel Open Source Technology Center>
[INFO   ] [GL          ] OpenGL renderer <Mesa DRI Intel(R) Haswell Mobile >
[INFO   ] [GL          ] OpenGL parsed version: 3, 0
[INFO   ] [GL          ] Shading version <1.30>
[INFO   ] [GL          ] Texture max size <8192>
[INFO   ] [GL          ] Texture max units <32>
[INFO   ] [Window      ] auto add sdl2 input provider
[INFO   ] [Window      ] virtual keyboard not allowed, single mode, not docked
invalid syntax (<string>, line 79)
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/tickeys-0.2.6-py2.7.egg/tickeys/run.py", line 14, in run_GUI
    from GUI import TickeysApp
  File "/usr/local/lib/python2.7/dist-packages/tickeys-0.2.6-py2.7.egg/tickeys/GUI.py", line 197, in <module>
    ''' % (_("Volume"), _("Pitch"), _("Sound Style"), _("Sound Style Items"), _("Start at startup"), _("Quit"), _("Hide"), _("Project Website"), _("Project Website"), _("Author"))).encode('utf-8'))
  File "/usr/lib/python2.7/dist-packages/kivy/lang.py", line 1796, in load_string
    parser = Parser(content=string, filename=fn)
  File "/usr/lib/python2.7/dist-packages/kivy/lang.py", line 1185, in __init__
    self.parse(content)
  File "/usr/lib/python2.7/dist-packages/kivy/lang.py", line 1291, in parse
    rule.precompile()
  File "/usr/lib/python2.7/dist-packages/kivy/lang.py", line 1049, in precompile
    x.precompile()
  File "/usr/lib/python2.7/dist-packages/kivy/lang.py", line 976, in precompile
    self.co_value = compile(value, self.ctx.filename or '<string>', mode)
  File "<string>", line 79
    Sound Style Items
              ^
SyntaxError: invalid syntax
Run GUI Fail, reason:

cc@CC:~$ sudo apt-get remove simplebackup
[sudo] password for cc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'simplebackup' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gir1.2-gmenu-3.0 gir1.2-keybinder-3.0 libkeybinder-3.0-0 oneconf
  oneconf-common python-aptdaemon python-aptdaemon.gtk3widgets python-attr
  python-bs4 python-cups python-debian python-debtagshw python-defer
  python-dirspec python-html5lib python-lxml python-oneconf python-pam
  python-pyasn1-modules python-serial python-service-identity
  python-twisted-bin python-twisted-core python-twisted-web
  python-ubuntu-sso-client python-xapian python3-oneconf
  python3-piston-mini-client software-center-aptdaemon-plugins
  ubuntu-sso-client
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

cc@CC:~$ sudo apt-get remove kazam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'kazam' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gir1.2-gmenu-3.0 gir1.2-keybinder-3.0 libkeybinder-3.0-0 oneconf
  oneconf-common python-aptdaemon python-aptdaemon.gtk3widgets python-attr
  python-bs4 python-cups python-debian python-debtagshw python-defer
  python-dirspec python-html5lib python-lxml python-oneconf python-pam
  python-pyasn1-modules python-serial python-service-identity
  python-twisted-bin python-twisted-core python-twisted-web
  python-ubuntu-sso-client python-xapian python3-oneconf
  python3-piston-mini-client software-center-aptdaemon-plugins
  ubuntu-sso-client
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cc@CC:~$ 


```

[ATTACH=CONFIG]271551[/ATTACH][ATTACH=CONFIG]271552[/ATTACH]

---

### Post by deadflowr on 2016-10-08
Did you compile and install them from source?
The package manager (apt|dpkg) doesn't know nor care about packages installed from source.
For the package manager to have seen packages installed from source you need to use  [checkinstall]("https://help.ubuntu.com/community/CheckInstall"), which basically creates a .deb binary that the package manager can then see and use in the way the package manager is designed to do so.

---

### Post by 243750496 on 2016-10-08
sorry it&#347; a python source code so is anthing diffent?

[ATTACH=CONFIG]271554[/ATTACH][ATTACH=CONFIG]271555[/ATTACH][ATTACH=CONFIG]271556[/ATTACH]

btw:i want to use bomi but use sudo auto-apt run ./configure not same as offical wiki said :¨If the dependencies are available, a dialog box opens and ask you to install them.¨
```
cc@CC:~/Downloads/bomi-0.9.11$ auto-apt run ./configure
Entering auto-apt mode: ./configure
Exit the command to leave auto-apt mode.
configure for Linux...
Checking for ffmpeg >= 2.4 ... yes
Checking for libass >= 0.12.1 ... no
'libass >= 0.12.1' package was not found.
cc@CC:~/Downloads/bomi-0.9.11$ sudo apt-get install libass-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libass-dev is already the newest version (0.13.1-1).
The following packages were automatically installed and are no longer required:
  gir1.2-gmenu-3.0 gir1.2-keybinder-3.0 libkeybinder-3.0-0 oneconf
  oneconf-common python-aptdaemon python-aptdaemon.gtk3widgets python-attr
  python-bs4 python-cups python-debian python-debtagshw python-defer
  python-dirspec python-html5lib python-lxml python-oneconf python-pam
  python-pyasn1-modules python-serial python-service-identity
  python-twisted-bin python-twisted-core python-twisted-web
  python-ubuntu-sso-client python-xapian python3-oneconf
  python3-piston-mini-client software-center-aptdaemon-plugins
  ubuntu-sso-client
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cc@CC:~/Downloads/bomi-0.9.11$ 

```

and i type 
```
cc@CC:~/Downloads/bomi-0.9.11$ sudo find / -name kazam
find: ‘/run/user/1000/gvfs’: Permission denied
/usr/local/share/kazam
/usr/local/bin/kazam
/usr/local/lib/python3.5/dist-packages/kazam
/home/cc/.config/kazam
```

and i do remove 
```

cc@CC:~/Downloads/bomi-0.9.11$ sudo rm -rf  '/usr/local/lib/python3.5/dist-packages/kazam'  '/usr/local/lib/python3.5/dist-packages/kazam-1.4.5.egg-info' 
cc@CC:~/Downloads/bomi-0.9.11$ sudo rm -rf /home/cc/.config/kazam
cc@CC:~/Downloads/bomi-0.9.11$ sudo rm -rf /usr/local/bin/kazam
cc@CC:~/Downloads/bomi-0.9.11$ sudo rm -rf /usr/local/share/kazam
cc@CC:~/Downloads/bomi-0.9.11$ kazam
The program 'kazam' is currently not installed. You can install it by typing:
sudo apt install kazam
cc@CC:~/Downloads/bomi-0.9.11$

```

but it still there stubbon like a zombire but then i try to use ubuntu software to remove but failed , then use Snaptic to reinstall then remove  the icon still there but cant run so i have get annoied and cant understand what happen to my system after install from source code

so anbody can help me out???

[ATTACH=CONFIG]271557[/ATTACH]

btw:how to remove source code installation???i mean if i can find my correct source code pacage

---

