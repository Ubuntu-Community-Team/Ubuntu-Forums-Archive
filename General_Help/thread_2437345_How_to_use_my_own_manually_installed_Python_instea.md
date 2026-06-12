---
title: "How to use my own manually installed Python instead of the default one from repo?"
date: 2020-02-22
forum: General Help
---

### Post by jiapei100 on 2020-02-22
Hi, all:

I prefer using the NEWEST Python, instead of some stale version, such as: Python2.7 or Python3.5 . So now, I had Python3.8.1 installed. Everything seems to be fine but if I do ```
sudo apt update
```, I'll obtain the following ERROR message:

```
Traceback (most recent call last):                 
  File "/usr/lib/cnf-update-db", line 8, in <module>
    from CommandNotFound.db.creator import DbCreator
ModuleNotFoundError: No module named 'CommandNotFound'
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code

```

It seems some part of Ubuntu is based on the default Python from repo? Can anybody give me a hand on how to solve this bug?

Thank you very much.
Pei

---

### Post by TheFu on 2020-02-22
You created the bug by not leaving the system python alone.  Put it back they way it was.

The best practice is to leave the system python for all system needs and use a tool like **pyenv** to manage the specific different versions and libraries/modules for those specific versions without impacting the system's needs.  If you don't like pyenv, there are probably a few other, similar tools.

Ruby has rbenv.
Perl has Perlbrew.
These are similar tools for those language development envs so we don't need to screw with the system versions.  Just be certain you learn to disable the pyenv version when doing system stuff and re-enable it when working on your glorious, bug free, code.

---

### Post by The Cog on 2020-02-22
You might be able to use apt to reinstall the package default version. If that fails then all I can think of is to reinstall. As TheFu says, use pyenv or virtualenv when using other python versions - don't go replacing the system version as this can break a large number of system utilities.

---

### Post by mörgæs on 2020-02-22
Ubuntu 20.04 comes with Python 3.8 by default. I'm sure the developers would like if you give it a spin and report bugs if any is found. 

If you have some space left you could install 20.04 in a dual boot, keeping your present version untouched as a back-up, possibly using Python in a virtual environment here.

---

### Post by jiapei100 on 2020-02-22
Failed to install **Python 3.8.1** under **pyenv**.

> &#10140;  ~ pyenv install -v 3.8.1
......
ERROR: Exception:
Traceback (most recent call last):
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_internal/cli/base_command.py", line 188, in main
    status = self.run(options, args)
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_internal/commands/install.py", line 286, in run
    with self._build_session(options) as session:
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_internal/cli/base_command.py", line 101, in _build_session
    session = PipSession(
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_internal/download.py", line 559, in __init__
    self.headers["User-Agent"] = user_agent()
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_internal/download.py", line 144, in user_agent
    zip(["name", "version", "id"], distro.linux_distribution()),
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_vendor/distro.py", line 122, in linux_distribution
    return _distro.linux_distribution(full_distribution_name)
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_vendor/distro.py", line 677, in linux_distribution
    self.version(),
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_vendor/distro.py", line 737, in version
    self.lsb_release_attr('release'),
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_vendor/distro.py", line 899, in lsb_release_attr
    return self._lsb_release_info.get(attribute, '')
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_vendor/distro.py", line 552, in __get__
    ret = obj.__dict__[self._fname] = self._f(obj)
  File "/tmp/tmp6a9wsa3z/pip-19.2.3-py2.py3-none-any.whl/pip/_vendor/distro.py", line 1012, in _lsb_release_info
    stdout = subprocess.check_output(cmd, stderr=devnull)
  File "/tmp/python-build.20200222120905.3660/Python-3.8.1/Lib/subprocess.py", line 411, in check_output
    return run(*popenargs, stdout=PIPE, timeout=timeout, check=True,
  File "/tmp/python-build.20200222120905.3660/Python-3.8.1/Lib/subprocess.py", line 512, in run
    raise CalledProcessError(retcode, process.args,
subprocess.CalledProcessError: Command '('lsb_release', '-a')' died with <Signals.SIGABRT: 6>.
Makefile:1186: recipe for target 'install' failed
make: *** [install] Error 2

BUILD FAILEDCould not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
Fatal Python error: Py_Initialize: Unable to get the locale encoding
ModuleNotFoundError: No module named 'encodings'

Current thread 0x00007f597cccd340 (most recent call first):
 ( using python-build 1.2.16-5-g7097f820)

Inspect or clean up the working tree at /tmp/python-build.20200222120905.3660
Results logged to /tmp/python-build.20200222120905.3660.log

Last 10 log lines:
subprocess.CalledProcessError: Command '('lsb_release', '-a')' died with <Signals.SIGABRT: 6>.
Makefile:1186: recipe for target 'install' failed
make: *** [install] Error 2
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
Fatal Python error: Py_Initialize: Unable to get the locale encoding
ModuleNotFoundError: No module named 'encodings'

Current thread 0x00007f597cccd340 (most recent call first):
&#10140;

---

### Post by dragonfly41 on 2020-02-22
There is also anaconda3/conda

[https://anaconda.org/anaconda/python](https://anaconda.org/anaconda/python)

---

### Post by TheFu on 2020-02-22
what OS version are you on?
which python is being used?
which pyenv is being used?

Has pyenv been setup correctly and initialized?

I did something like this last month and don't remember any issues.

---

### Post by monkeybrain20122 on 2020-02-23
There are several options

1) conda see #6

2)python virtualenv. But if the existing python is 3.x, virtualenv only allows you to install different minor versions 3.x.y. That's why your attempt failed.

3)compile python from source locally in a folder in $HOME
and then use a script to set environmental variable when invoke your version of python.  e.g I am using python-3.7.6 for development on Ubuntu 16.04

```
$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:    16.04
Codename:    xenial

$which python3
/usr/bin/python3

$python3 --version
Python 3.5.2

$source ~/Scripts/python37.conf

$which python
/home/monkeybrain/opt/python37/bin/python

$ python --version
Python 3.7.6


```


Here is my script "python37.conf"
```

export PREFIX=/home/monkeybrain/opt/python37
export HOME=$PREFIX #for spyder to create seperate config file 
export PATH=$PREFIX/bin:$PATH
export LD_LIBRARY_PATH=$PREFIX/lib:$LD_LIBRARY_PATH
export PYTHONUSERBASE=$PREFIX
export PYTHONPATH=$PREFIX/lib/python3.7/site-packages:$PYTHONPATH
```

I prefer 3 since it is most clean and elegant without having to install off a preexisting python like pyenv and doesn't require installing a lot of unneeded packages like conda. I can run unlimited versions of pythons this way, just install each python in a different folder and create a pythonXX.conf for each version.

How to compile python. get the pythonXY [tarball]("https://www.python.org/downloads/"), untar

```
source ~/Scripts/pythonXY.conf
cd Python-XY

./configure --prefix=$PREFIX --enable-ipv6 --enable-shared --enable-optimizations --enable-loadable-sqlite-extensions --with-dbmliborder=bdb:gdbm --with-computed-gotos --enable-big-digits
make -j8
make test -j8
make install -j8
```

---

