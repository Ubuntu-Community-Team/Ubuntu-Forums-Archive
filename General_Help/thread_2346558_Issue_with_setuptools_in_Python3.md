---
title: "Issue with setuptools in Python3"
date: 2016-12-16
forum: General Help
---

### Post by jumblie on 2016-12-16
Hi,

*Background:*

I am trying to upgrade mnemosyne  ([http://mnemosyne-proj.org/](http://mnemosyne-proj.org/)). I had to install Python3 (a named dependency; the code for mnemosyne has as of this upgrade moved to Python3). I've had no issue with  previous upgrades and so believe this issue may be related to Python3.

I am running Ubuntu 14.04 LTS and am  admittedly a little out of my depth here. No doubt there is not enough  info here to find a solution, so please ask and I will update with new  info.

*The Issue:*

When executing setup.py with:

```
sudo python3 setup.py install
```

I am coming up against the following error.

```
Traceback (most recent call last):
  File "setup.py", line 2, in <module>
    from setuptools import setup, Command
ImportError: No module named 'setuptools'
```

I have read  widely and tried a heap of suggestions and have narrowly avoided  trashing my Ubuntu install. These include;

```
sudo apt-get install python3-setuptools
sudo apt-get install python3-pip
sudo pip3 install --upgrade setuptools

```

Python3 info:
```
which python3
/usr/local/bin/python3
```

Thanks in advance.

---

### Post by dragonfly41 on 2016-12-16
To avoid you having to "trash your Ubuntu installation", if it helps you, the package installs o.k. on my Ubuntu 14.04 .. although I don't really need it ..

For some reason ("security token missing") I can't post the full installation log in code block.

I would check your python3 environment / path etc.

Here is mine ..

python3 --version
Python 3.4.3

which python3
/usr/bin/python3

[Later thought]

Do you have read/write permissions here .. /usr/local/lib/python3.4/dist-packages/

---

### Post by jumblie on 2016-12-16
Thanks dragonfly41...

> the package installs o.k. on my Ubuntu 14.04 .. although I don't really need it ..

Are you referring to the package mnemosyne? I have managed to install python3, python3-pip and python3-setuptools error free.

> 
python3 --version
Python 3.4.3

which python3
/usr/bin/python3

Here are mine...

```
python3 --version
Python 3.5.2

which python3
/usr/local/bin/python3

```

The path may be an issue being in ***/usr/local/bin*** rather than ***/usr/bin*** but I'm not too sure how to progress with that.

> Do you have read/write permissions here .. /usr/local/lib/python3.4/dist-packages/

I've now changed them (recursively) to the below - I am a member of *mygroup* - (but still no dice):

```
/usr/local/lib/python3.4$ ls -l
total 4
drwxrwsr-x 7 root mygroup 4096 Dec 16 21:55 dist-packages
```

It could very well still be a path and/or permissions issue.

---

### Post by dragonfly41 on 2016-12-17
I simply downloaded M[COLOR=#000000]nemosyne-2.4.tar.gz and unzipped into /opt directory.
[/COLOR]
My 14.04 (32bit) is full of various development experiments (python, Qt5 etc) so I might not be the best adviser for your problem. 

I have myself quite a few problems switching between python2.7 and python3.4.

I note that in your installation

python3 --version command shows 3.5.2 .. however you also refer to /usr/local/lib/python3.4.

Do you have multiple python installations?

Some more commands to try .. 

```

echo $pythonpath

which pip

which pip3


```

When I try to launch installed mnemosyne I see this .. so it is not fully installed yet ..
```

File "/usr/local/lib/python3.4/dist-packages/Mnemosyne-2.4-py3.4.egg/EGG-INFO/scripts/mnemosyne", line 132, in <module>
 RuntimeError: the sip module implements API v11.0 but the PyQt5.QtWebEngineWidgets module requires API v11.3
An unexpected error has occurred.

```

I see that I have to upgrade.

I'll try again running mnemosyne after checking pip3 installation.

Incidentally I set PYTHONPATH in ~/.profile


And checking pip3 ...

```

pip3 install -U pip3

You are using pip version 8.1.2, however version 9.0.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.

```

---

### Post by jumblie on 2016-12-18
Well, when I first came upon this problem, I started searching for answers. Not that I get it all now, but when I started I knew even less! In desperation, I tried heaps of things without really knowing what I was doing.

As a result, I installed many packages from different sources... eg: from apt-get and also from python.org directly. What this means is I have now been left with a dogs breakfast, including what seems to be both **python3.4** and **python3.5**. Add to this various attempts at pip, setuptools et al and you can begin to appreciate the mess I'm in. I don't really know what's what, I may actually have everything I need but its just misconfigured.

I guess that's a really long way of saying there is likely more than one version of all the packages required and thought it was worthwhile shedding some light on the complexity of the mess I have created.

Not that I think its relevant, but since you've mentioned it, I'm on the **64 bit version of 14.04 LTS**.

> python3 --version command shows 3.5.2 .. however you also refer to /usr/local/lib/python3.4.

Do you have multiple python installations?

As per above, sadly yes. As per my previous post I added read/write permissions to ..** /usr/local/lib/python3.4/dist-packages/** which I now realise is futile as I'm actually using **3.5**.

```
python3 --version
Python 3.5.2

which python3
/usr/local/bin/python3
```

As it turns out, python3.5 doesn't have a *dist-packages* but does have a *distutils* so I have made sure I have read/write permissions for that (just in case) but alas, it made no difference.

echo $pythonpath is blank but...

```
python -c "import sys; print(sys.path)"
''
'/usr/lib/python2.7'
'/usr/lib/python2.7/plat-x86_64-linux-gnu'
'/usr/lib/python2.7/lib-tk'
'/usr/lib/python2.7/lib-old'
'/usr/lib/python2.7/lib-dynload'
'/usr/local/lib/python2.7/dist-packages'
'/usr/local/lib/python2.7/dist-packages/Mnemosyne-2.3.6-py2.7.egg'
'/usr/local/lib/python2.7/dist-packages/CherryPy-8.1.2-py2.7.egg'
'/usr/local/lib/python2.7/dist-packages/WebOb-1.6.3-py2.7.egg'
'/usr/local/lib/python2.7/dist-packages/setuptools-30.3.0-py2.7.egg'
'/usr/local/lib/python2.7/dist-packages/pip-9.0.1-py2.7.egg'
'/usr/lib/python2.7/dist-packages'
'/usr/lib/python2.7/dist-packages/PILcompat'
'/usr/lib/python2.7/dist-packages/gtk-2.0'
'/usr/lib/pymodules/python2.7'
'/usr/lib/python2.7/dist-packages/ubuntu-sso-client'

python3 -c "import sys; print(sys.path)"
''
'/usr/local/lib/python35.zip'
'/usr/local/lib/python3.5'
'/usr/local/lib/python3.5/plat-linux'
'/usr/local/lib/python3.5/lib-dynload'
'/home/jumblut/.local/lib/python3.5/site-packages'
'/usr/local/lib/python3.5/site-packages'
```

```
which pip
/usr/local/bin/pip

which pip3
/usr/local/bin/pip3

pip3 --version
pip 9.0.1 from /usr/local/lib/python3.4/dist-packages/pip-9.0.1-py3.4.egg (python 3.4)
```

I observe pip3 is associated with **python3.4** and not **python3.5**, I assume this is an issue? At least its the right version! :)

Oh, and I'm afraid that;

> Incidentally I set PYTHONPATH in ~/.profile means nothing to me. :(

---

### Post by dragonfly41 on 2016-12-18
I have a similar "dog's breakfast&#8221; in my experiments with Python 2 and 3 and Qt5.

From your above post it seems clear now that you installed mnemosyne using python default 2.7 rather than python3.

```

'/usr/local/lib/python2.7/dist-packages/Mnemosyne-2.3.6-py2.7.egg'

```

Go back to your Mnemosyne download and try forcing installation via python3 by running

python3 setup.py install   .. (not python setup.py install which will use default python2.7).

I see in first post that in fact you used [COLOR=#000000][FONT=Ubuntu Mono]sudo python3 setup.py install .. but are you sure?[/FONT][/COLOR]

Then again run .. python3 -c "import sys; print(sys.path)"

PYTHONPATH is used to define the paths for importing python modules but it is better if you don't need to use it.

Where needed user environment vars can be set in ~/.profile (hidden file).

---

### Post by jumblie on 2016-12-18
> 
'/usr/local/lib/python2.7/dist-packages/Mnemosyne-2.3.6-py2.7.egg'


The above snippet actually refers to my existing (working) Mnemosyne install. This issue is a result of me trying to **upgrade** from **2.3.6** to **2.4**.

I doubt **Mnemosyne 2.4** will install with **python** as **python3** is a dependency.

---

### Post by dragonfly41 on 2016-12-18
Sorry, I missed the point that you are trying an upgrade.
You might need to setup an alias for one of your installations if you retain both versions.
e.g. mnemosyne2 and mnemosyne3

However back to  the main issue.  In my reading I see that I have problems with sip.
I have older version installed.

Download ...

[https://sourceforge.net/projects/pyqt/files/sip/sip-4.18.1/sip-4.18.1.tar.gz/download](https://sourceforge.net/projects/pyqt/files/sip/sip-4.18.1/sip-4.18.1.tar.gz/download)

Sip installation instructions here ...

[http://pyqt.sourceforge.net/Docs/sip4/installation.html](http://pyqt.sourceforge.net/Docs/sip4/installation.html)

Saved in ..

~/sip-4.18.1

ran ```
python3 configure.py
```

then I read suggestions here ..

[http://stackoverflow.com/questions/22589497/pyqt5-sip-api-10-level-error-api-11-required](http://stackoverflow.com/questions/22589497/pyqt5-sip-api-10-level-error-api-11-required)

```

[COLOR=#242729]dpkg -l | grep sip[/COLOR]

ii  python-sip                                                  4.15.5-1build1                                       i386         Python/C++ bindings generator runtime library
ii  python3-sip                                                 4.15.5-1build1                                       i386         Python 3/C++ bindings generator runtime library

sip -V
4.18.1

```

Note the difference in version.

So I'm currently trying to upgrade sip 4.15.5 to latest 4.18.1
And I have run the command ...

[COLOR=#242729][FONT=Consolas]```

sudo apt-get purge python3-sip python3-sip-dev
[/FONT][/COLOR]
```

but that applies major surgery and sip 4.18.1 has to be reinstalled.

```

python3 -c "import sip; print(sip, sip.SIP_VERSION_STR)"

```

I'll come back when I've finally purged old version of sip and have the latest.

---

### Post by dragonfly41 on 2016-12-18
I have been experimenting further.
This installation problem might arise from Qt5 dependency.

..

If you read the README.md file for Mac/OS (although you don't have Mac) it suggests setting path to Qt5.

```

     export PYTHON=python3
     export QT5DIR=/usr/local/opt/qt5 # help pyinstaller find the qt5 path
     // ignore the rest which is for Mac only

```

Read here to find Qt version you have installed .. 
[https://harishnavnit.wordpress.com/2014/03/24/handling-multiple-versions-of-qt/](https://harishnavnit.wordpress.com/2014/03/24/handling-multiple-versions-of-qt/)

Try running these commands and  check default version of Qt installed

```
qmake -v
```

returns this for me ..

```
QMake version 3.0
Using Qt version 5.6.0 in /opt/qt56/lib
```

Now before running the make command (in [COLOR=#000000]mnemosyne folder)[/COLOR], first *predefine* path to Qt5 by running this command (edit the path to reflect your own installation found from qmake -v).

```
export QT5DIR=/opt/qt56
``` .. insert your* own* path to qt5x

followed by

```
make && make install
```

You should see extra clues in a popup.

---

### Post by jumblie on 2016-12-19
UPDATE: After a ton of stuffing around, installing a bunch of different packages, I finally had success by recompiling the source for python3.5. I've now managed to successfully **install **mnemosyne but I've got other issues related to a module named 'PIL' and it won't run!

I'll endeavour to post my summarised learnings here soon. Thanks dragonfly41 for all your input, much appreciated, it certainly helped.

---

### Post by dragonfly41 on 2016-12-19
Well this troubleshooting exercise has helped me too in sorting out a pile of inconsistencies.
I have a series of dev installations of Python and Qt5 and I suspect that I need to purge some older versions.
I got as far as the make command but then hit this ...

```

This application failed to start because it could not find or load the Qt platform plugin "xcb"
in "".

```

I think I'll try updating to python3.5 and clear out other python3 variants I have installed.

I found this interesting ... look at easy-install.pth file ...

[http://blog.olgabotvinnik.com/blog/2014/03/03/2014-03-03-pythonpath-is-a-liar-site-py-and-easy-install-pth-tell/](http://blog.olgabotvinnik.com/blog/2014/03/03/2014-03-03-pythonpath-is-a-liar-site-py-and-easy-install-pth-tell/)

---

### Post by jumblie on 2016-12-19
@dragonfly41 - I'm glad you've managed to get something out of this torturous exercise!

A couple of things; if you're going to python3.5 you'll have to compile from source because its not available in the repos (apt-get) for Ubuntu 14.04. Also, make sure you install everything you'll need BEFORE compiling python, otherwise you'll need to recompile... I'll endeavour to expand more on this in my next post.

Good luck with clearing out other Python variants... but be warned: I attempted to remove python 3.4 with apt-get remove and nearly bricked my system despite already having python3.5 and python3 pointing to it (I aborted when things started disappearing off the desktop!!!). I'll be interested to hear how you go about it.

---

### Post by dragonfly41 on 2016-12-20
You wrote earlier ..

> [COLOR=#000000]I finally had success by recompiling the source for python3.5 [/COLOR]

Now I've been trying with Python-3.5.2 download and compiling python3.5 and experiencing a roadblock. So I would like to compare notes.

Reading some blogs including this one ... [http://tecadmin.net/install-python-3-5-on-ubuntu/](http://tecadmin.net/install-python-3-5-on-ubuntu/)
I installed these packages ... via Synaptic Package Manager .. then checked all of them.

```

build-essential is already the newest version.
checkinstall is already the newest version.
libreadline-gplv2-dev is already the newest version.
libncursesw5-dev is already the newest version.
libssl-dev is already the newest version.
libsqlite3-dev is already the newest version.
tk-dev is already the newest version.
libc6-dev is already the newest version.
libbz2-dev is already the newest version.
libgdbm-dev is already the newest version.

```

I get to the end of running **sudo ./configure** .. in Python-3.5.2 source folder which I created from a download.

```

...
...
creating Modules/Setup
creating Modules/Setup.local
creating Makefile

```

...

Next I run **sudo make altinstall** (and this is wnen I encounter errors at the end of log)

```


long list of checks
...
...
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: error: cannot find input file: `include/Makefile.in'
Failed to configure _ctypes module
*** WARNING: renaming "_ctypes" since importing it failed: build/lib.linux-i686-3.5/_ctypes.cpython-35m-i386-linux-gnu.so: cannot open shared object file: No such file or directory
error: [Errno 2] No such file or directory: 'build/lib.linux-i686-3.5/_ctypes.cpython-35m-i386-linux-gnu.so' -> 'build/lib.linux-i686-3.5/_ctypes.cpython-35m-i386-linux-gnu_failed.so'
make: *** [sharedmods] Error 1

```


Can you see any steps/packages I have missed?  I've searched around to try to fathom out why there is no _ctypes module found ...

build/lib.linux-i686-3.5/_ctypes.cpython-35m-i386-linux-gnu.so

[p.s.] I recollect that I am on 32bit and you are on 64bit so you may not see i386 files.

---

### Post by dragonfly41 on 2016-12-20
I think that I need a 32bit version of Python-3.5.2. 

Does anyone have the download link for 32bit Python-3.5.2 source?

I found one for Windows, [https://chocolatey.org/packages/python3-x86_32](https://chocolatey.org/packages/python3-x86_32)
but not yet Linux/Ubuntu.   
I guess my old 32bit laptop is becoming dated.

---

### Post by dragonfly41 on 2016-12-22
For the record .. I found Miniconda (a subset of Anaconda)

[http://conda.pydata.org/miniconda.html](http://conda.pydata.org/miniconda.html)

Installed Python-3.5.2 (32bits) Linux.

---

### Post by jumblie on 2016-12-22
Hey dragonfly41, how did you go?

I have now finally managed to resolve all issues and upgrade Mnemosyne to 2.4!

After a lot of trial and error, I think this is what I should have done from the beginning:

Check the version available in the repos:```
apt-cache policy <package name>
``` This is a great way of avoiding the mess of having multiple versions of the same package installed, especially Python. It is also fundamental to work out whether you can install via the repos or if you have to track down the source code for the version you are after.

In this case, Python3.5 is not available from the repos for Ubuntu 14.04 LTS so you need to download and compile the source code... but first, you need to install the required dependencies:

```
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils
```

Download and compile the source code for your Python version of choice from [python.org]("https://www.python.org/downloads/"). Compile instructions are normally found in the readme.

Verify your version of Python with:
```
python -V

python3 -V
```

for Python 2.x and Python 3.x respectively.

Install pip (a tool for installing and managing Python packages) with: ```
wget [https://bootstrap.pypa.io/get-pip.py](https://bootstrap.pypa.io/get-pip.py) -O - | sudo python3
```

Check pip corresponds to your version of Python: ```
pip3 --version
```

Finally, install setuptools with: ```
wget [https://bootstrap.pypa.io/ez_setup.py](https://bootstrap.pypa.io/ez_setup.py) -O - | sudo python3
```

---

### Post by dragonfly41 on 2016-12-23
@jumblie

As I wrote in post #15 while I was experimenting with mixed python installations I found ... miniconda ...
[http://conda.pydata.org/docs/install/quick.html](http://conda.pydata.org/docs/install/quick.html)

This really removes many headaches arising from mixed versions.

There are two versions of miniconda for download .. as bash installer scripts

miniconda2 which installs Python 2.7 by default
miniconda3 which installs Python 3.5 by default

I chose miniconda3 on my Ubuntu 14.04 (32bit) setup then created a Python 2.7 (32 bit) env using conda commands.
But if miniconda2 is installed you can still create a Python 3.5 env.

So I can now easily switch between python versions.
Note that pip, pip3 is also installed by conda.

I will eventually clear out my earlier installations of Python 2.7 and 3.5 and stick with only miniconda (and perhaps upgrade later to Anaconda when I have more RAM).

I have not yet installed [COLOR=#000000]Mnemosyne 2.4 since I've been focussing on experiments with Miniconda.[/COLOR]

Miniconda makes installations of packages very easy.

I do recommend this approach.   I wish I had found it earlier.

---

### Post by jumblie on 2016-12-23
@dragonfly41

Good stuff and good to know! As is always the case, everything is easier in hindsight! :P Thanks for all your help.

---

