---
title: "How to Install PyObjC?"
date: 2013-06-10
forum: General Help
---

### Post by mark2741 on 2013-06-10
I am trying to install "The Maker" CMS - [http://makercms.org/](http://makercms.org/)

It is open source. It is targeted for use on Mac OS X but while listening to the latest FLOSS Weekly podcast the hosts said they were able to install it on Ubuntu easily. Unfortunately it's not so easy for me :mad:

The dependencies for it are:

*******************
**Requirements**

To run TheMaker from source using Python you need:

    Python 2.7
    wxPython 2.9.4.0 (Cocoa build for OS X)
    python-markdown2 [http://code.google.com/p/python-markdown2/](http://code.google.com/p/python-markdown2/)
    PyObjC [http://pythonhosted.org/pyobjc/install.html](http://pythonhosted.org/pyobjc/install.html)

*********************

I got everything going except for PyObjC. wxPython and Markdown2 were pretty easy to install. But I can't get PyObjC installed. 

I first installed "easy_install" for Python and then tried: 

easy_install -U pyobjc-core

But that results in this error:

*********************
mark@mark-ubuntu:~/Desktop/the-maker-master$ easy_install -U pyobjc
error: can't create or remove files in install directory

The following error occurred while trying to add or remove files in the
installation directory:

    [Errno 13] Permission denied: '/usr/local/lib/python2.7/dist-packages/test-easy-install-5893.pth'

The installation directory you specified (via --install-dir, --prefix, or
the distutils default setting) was:

    /usr/local/lib/python2.7/dist-packages/

Perhaps your account does not have write access to this directory?  If the
installation directory is a system-owned directory, you may need to sign in
as the administrator or "root" account.  If you do not have administrative
access to this machine, you may wish to choose a different installation
directory, preferably one that is listed in your PYTHONPATH environment
variable.

For information on other options, you may wish to consult the
documentation at:

  [http://packages.python.org/distribute/easy_install.html](http://packages.python.org/distribute/easy_install.html)

Please make the appropriate changes for your system and try again.

mark@mark-ubuntu:~/Desktop/the-maker-master$ 
***************************************

So then I tried the same command but as sudo, and got this:

***************************************
mark@mark-ubuntu:~/Desktop/the-maker-master$ sudo easy_install -U pyobjc
[sudo] password for mark: 
Searching for pyobjc
Reading [http://pypi.python.org/simple/pyobjc/](http://pypi.python.org/simple/pyobjc/)
Best match: pyobjc 2.5.1
Downloading [http://pypi.python.org/packages/source/p/pyobjc/pyobjc-2.5.1.tar.gz#md5=f242cff4a25ce397bb381c21a35db885](http://pypi.python.org/packages/source/p/pyobjc/pyobjc-2.5.1.tar.gz#md5=f242cff4a25ce397bb381c21a35db885)
Processing pyobjc-2.5.1.tar.gz
Writing /tmp/easy_install-WXPQtl/pyobjc-2.5.1/setup.cfg
Running pyobjc-2.5.1/setup.py -q bdist_egg --dist-dir /tmp/easy_install-WXPQtl/pyobjc-2.5.1/egg-dist-tmp-gX_FWn
Traceback (most recent call last):
  File "/usr/bin/easy_install", line 9, in <module>
    load_entry_point('distribute==0.6.34', 'console_scripts', 'easy_install')()
  File "/usr/lib/python2.7/dist-packages/setuptools/command/easy_install.py", line 1985, in main
    with_ei_usage(lambda:
  File "/usr/lib/python2.7/dist-packages/setuptools/command/easy_install.py", line 1966, in with_ei_usage
    return f()
  File "/usr/lib/python2.7/dist-packages/setuptools/command/easy_install.py", line 1989, in <lambda>
    distclass=DistributionWithoutHelpCommands, **kw
  File "/usr/lib/python2.7/distutils/core.py", line 152, in setup
    dist.run_commands()
  File "/usr/lib/python2.7/distutils/dist.py", line 953, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.7/distutils/dist.py", line 972, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.7/dist-packages/setuptools/command/easy_install.py", line 377, in run
    self.easy_install(spec, not self.no_deps)
  File "/usr/lib/python2.7/dist-packages/setuptools/command/easy_install.py", line 617, in easy_install
    return self.install_item(spec, dist.location, tmpdir, deps)
  File "/usr/lib/python2.7/dist-packages/setuptools/command/easy_install.py", line 647, in install_item
    dists = self.install_eggs(spec, download, tmpdir)
  File "/usr/lib/python2.7/dist-packages/setuptools/command/easy_install.py", line 842, in install_eggs
    return self.build_and_install(setup_script, setup_base)
  File "/usr/lib/python2.7/dist-packages/setuptools/command/easy_install.py", line 1122, in build_and_install
    self.run_setup(setup_script, setup_base, args)
  File "/usr/lib/python2.7/dist-packages/setuptools/command/easy_install.py", line 1108, in run_setup
    run_setup(setup_script, args)
  File "/usr/lib/python2.7/dist-packages/setuptools/sandbox.py", line 33, in run_setup
    lambda: execfile(
  File "/usr/lib/python2.7/dist-packages/setuptools/sandbox.py", line 81, in run
    return func()
  File "/usr/lib/python2.7/dist-packages/setuptools/sandbox.py", line 35, in <lambda>
    {'__file__':setup_script, '__name__':'__main__'}
  File "setup.py", line 90, in <module>
    
ValueError: invalid literal for int() with base 10: ''
mark@mark-ubuntu:~/Desktop/the-maker-master$ 
***************************************

Help! Would love to try this program on Ubuntu.

---

