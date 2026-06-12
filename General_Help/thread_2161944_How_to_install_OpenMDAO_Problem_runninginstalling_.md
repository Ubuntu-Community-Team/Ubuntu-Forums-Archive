---
title: "How to install OpenMDAO? Problem running/installing go-openmdao.py"
date: 2013-07-12
forum: General Help
---

### Post by lprofil on 2013-07-12
Hallo,

i'd like to use OpenMDAO so i went to:
[http://openmdao.org/docs/getting-started/requirements.html](http://openmdao.org/docs/getting-started/requirements.html)

and installed the packaeges:

```
sudo aptitude install -y python-dev python-numpy python-scipy python-matplotlib gfortran
```

i try to run: 

```
python go-openmdao.py
```

but what i see is a incomplete installation like this:

```
user@pc:~/Desktop/webcam-pulse-detector-master$ python go-openmdao.py
New python executable in openmdao-0.7.0/bin/python
Traceback (most recent call last):
  File "go-openmdao.py", line 2908, in <module>
    main()
  File "go-openmdao.py", line 966, in main
    never_download=options.never_download)
  File "go-openmdao.py", line 1067, in create_environment
    site_packages=site_packages, clear=clear))
  File "go-openmdao.py", line 1361, in install_python
    shutil.copyfile(executable, py_executable)
  File "/usr/lib/python2.7/shutil.py", line 83, in copyfile
    with open(dst, 'wb') as fdst:
IOError: [Errno 40] Too many levels of symbolic links: 'openmdao-0.7.0/bin/python'

```

Can anybody please explain why this is happening?

Thanks in advance!

/lprofil

---

### Post by oldos2er on 2013-07-12
Moved to General Help.

---

