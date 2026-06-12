---
title: "Can't install PyQWT version 5.2.0"
date: 2014-03-09
forum: General Help
---

### Post by Muhammad_Al_Ikhsan on 2014-03-09
Hello All Member Ubuntu forums ,

Today i'm try to install my New NooElec R820T SDR & CVB-T NETSDR Mini (Usb Stick RTL-SDR). I'm follow guide in this site :
> [http://gnuradio.org/redmine/projects/gnuradio/wiki/UbuntuInstall](http://gnuradio.org/redmine/projects/gnuradio/wiki/UbuntuInstall)
That site tell me to [COLOR=#303030][FONT=Verdana]Download and install PyQWT version 5.2.0[/FONT][/COLOR]
[http://pyqwt.sourceforge.net/download.html](http://pyqwt.sourceforge.net/download.html)

After i download and extract that :
 $ tar xzf PyQwt-5.2.0.tar.gz
   $ cd PyQwt-5.2.0/configure
   $ ./configure.py -Q ../qwt-5.2 --module-install-path=/opt/qt/lib/python2.7/dist-packages/PyQt4/Qwt5
   $ make
   $ sudo make installThen i got an error in my terminal like this :
```
ikhsan@Acer:~/sdr/PyQwt-5.2.0/configure$ sudo ./configure.py -Q ../qwt-5.2 --module-install-path=/opt/qt/lib/python2.7/dist-packages/PyQt4/Qwt5
[sudo] password for ikhsan: 
Command line options:
{'debug': False,
 'disable_numarray': False,
 'disable_numeric': False,
 'disable_numpy': False,
 'excluded_features': [],
 'extra_cflags': [],
 'extra_cxxflags': [],
 'extra_defines': [],
 'extra_include_dirs': [],
 'extra_lflags': [],
 'extra_lib_dirs': [],
 'extra_libs': [],
 'jobs': '',
 'module_install_path': '/opt/qt/lib/python2.7/dist-packages/PyQt4/Qwt5',
 'modules': [],
 'qt': 4,
 'qwt_sources': '../qwt-5.2',
 'sip_include_dirs': [],
 'subdirs': [],
 'timelines': [],
 'trace': ''}


Found SIP-4.15.4.
Found 'posix' operating system:
2.7.3 (default, Jan  2 2013, 16:53:07) 
[GCC 4.7.2]
Do not get upset by error messages in the next 3 compiler checks:
Check if 'size_t' and 'unsigned int' are the same type:
An internal error occured.  Please report all the output
from the program, including the following traceback, to
pyqwt-users@lists.sourceforge.net
Traceback (most recent call last):
  File "./configure.py", line 1107, in <module>
    main()
  File "./configure.py", line 1078, in main
    options = check_compiler(configuration, options)
  File "./configure.py", line 422, in check_compiler
    if compile_qt_program(name, configuration):
  File "./configure.py", line 118, in compile_qt_program
    exe, build = makefile.build_command(name)
  File "/usr/lib/python2.7/dist-packages/sipconfig.py", line 1986, in build_command
    build.extend(self.optional_list("CXXFLAGS_APP"))
  File "/usr/lib/python2.7/dist-packages/sipconfig.py", line 1006, in optional_list
    return self.__dict__[name].as_list()
KeyError: 'CXXFLAGS_APP'
ikhsan@Acer:~/sdr/PyQwt-5.2.0/configure$ 

```

how i can fix this error :(

---

### Post by Muhammad_Al_Ikhsan on 2014-03-11
Up help me please :(

---

