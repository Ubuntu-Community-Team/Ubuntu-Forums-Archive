---
title: "how to uninstall software installed with pip"
date: 2015-03-03
forum: General Help
---

### Post by rebeltaz on 2015-03-03
I installed an older version of Electrum since the latest isn't compatible with Ubuntu 10.04 and apparently the one I selected isn't either. At least it installs, but it fails to run. Anyway... I installed this with 'sudo pip install [https://download.electrum.org/Electrum-1.9.tar.gz](https://download.electrum.org/Electrum-1.9.tar.gz)' but I cannot figure out how to uninstall it. I tried 'sudo pip uninstall electrum' but I get an error: "pip: error: No command by the name pip uninstall".

---

### Post by CantankRus on 2015-03-03
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **pip --help**

Usage:   
  pip <command> [options]

Commands:
  install                     Install packages.
  uninstall                   Uninstall packages.
  freeze                      Output installed packages in requirements format.
  list                        List installed packages.
  show                        Show information about installed packages.
  search                      Search PyPI for packages.
  wheel                       Build wheels from your requirements.
  zip                         DEPRECATED. Zip individual packages.
  unzip                       DEPRECATED. Unzip individual packages.
  bundle                      DEPRECATED. Create pybundles.
  help                        Show help for commands.

General Options:
  -h, --help                  Show help.
  -v, --verbose               Give more output. Option is additive, and can be used up to 3 times.
  -V, --version               Show version and exit.
  -q, --quiet                 Give less output.
  --log-file <path>           Path to a verbose non-appending log, that only logs failures. This log is active
                              by default at /home/glen/.pip/pip.log.
  --log <path>                Path to a verbose appending log. This log is inactive by default.
  --proxy <proxy>             Specify a proxy in the form [user:passwd@]proxy.server:port.
  --timeout <sec>             Set the socket timeout (default 15 seconds).
  --exists-action <action>    Default action when a path already exists: (s)witch, (i)gnore, (w)ipe, (b)ackup.
  --cert <path>               Path to alternate CA bundle.
```

What do these commands show?
```
pip search electrum
pip show electrum
```

---

### Post by rebeltaz on 2015-03-03
Yeah... I did try the --help option before posting:
```

derek@shop:~$ pip --help
Usage: pip COMMAND [OPTIONS]

Options:
  --version             show program's version number and exit
  -h, --help            Show help
  -E DIR, --environment=DIR
                        virtualenv environment to run pip in (either give the
                        interpreter or the environment base directory)
  -v, --verbose         Give more output
  -q, --quiet           Give less output
  --log=FILENAME        Log file where a complete (maximum verbosity) record
                        will be kept
  --proxy=PROXY         Specify a proxy in the form
                        user:passwd@proxy.server:port. Note that the
                        user:password@ is optional and required only if you
                        are behind an authenticated proxy.  If you provide
                        user@proxy.server:port then you will be prompted for a
                        password.
  --timeout=SECONDS     Set the socket timeout (default 15 seconds)

Commands available:
  bundle: Create pybundles (archives containing multiple packages)
  freeze: Put all currently installed packages (exact versions) into a requirements file
  help: Show available commands
  install: Install packages
  unzip: Unzip individual packages
  zip: Zip individual packages

```

In light of that... both commands you requested show the same error:
```

Usage: pip COMMAND [OPTIONS]

pip: error: No command by the name pip show

```

---

### Post by CantankRus on 2015-03-03
Command shows package that installed the **pip** command. (I'm using Ubuntu Trusty)
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **dpkg -S $(which pip)**
python-pip: /usr/bin/pip
```

```
[COLOR="#008000"]**glen@Trusty:~$**[/COLOR] **pip search electrum**
reddcoin-electrum         - Reddcoin Electrum wallets for desktop
reddcoin-electrum-server  - Reddcoin Electrum server
electrum                  - Lightweight Bitcoin Wallet
```

---

### Post by rebeltaz on 2015-03-03
Same repsonse as you... 
```

derek@shop:~$ dpkg -S $(which pip)
python-pip: /usr/bin/pip

```

I'm using 10.04 on this computer, though...
```

derek@shop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

```

---

### Post by CantankRus on 2015-03-03
Yeah, I've only used pip to install a couple of scripts from github so no real expert ....
eg
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] sudo pip install gkeyring**
Downloading/unpacking gkeyring
  Downloading gkeyring-0.3.tar.gz
  Running setup.py (path:/tmp/pip_build_root/gkeyring/setup.py) egg_info for package gkeyring
    
Installing collected packages: gkeyring
  Running setup.py install for gkeyring
    
    Installing gkeyring script to /usr/local/bin
Successfully installed gkeyring
Cleaning up...
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] sudo pip uninstall gkeyring**
Uninstalling gkeyring:
  /usr/local/bin/gkeyring
  /usr/local/lib/python2.7/dist-packages/gkeyring-0.3.egg-info
  /usr/local/lib/python2.7/dist-packages/gkeyring.py
  /usr/local/lib/python2.7/dist-packages/gkeyring.pyc
Proceed (y/n)?
```

[**_[COLOR="#B22222"]Docs » Reference Guide » pip uninstall[/COLOR]_**]("https://pip.pypa.io/en/latest/reference/pip_uninstall.html")

---

### Post by sammiev on 2015-03-03
10.04 is dead at this point, isn't?
10.04 server is good for 1 more month.

---

### Post by rebeltaz on 2015-03-03
> **sammiev said:**
> 10.04 is dead at this point, isn't?
10.04 server is good for 1 more month.

lol... yeah, so I've been told. But I am of the belief that "if it ain't broke, don't fix it." On the computers on which I HAVE to run Windoze, I still run XP. Instead of a "smartphone," I still use an HP iPAQ. To take pictures, I still use a camera. And to take notes, beleive it or not, I still use.... gasp! a PENCIL and PAPER! lol :D

In my opinion, newer does not always equate with better.

And yes, I see the irony of that in light of the trouble I am having with this one issue, but I find it hard to believe that something that (back in 10.04's day) could be installed could not be uninstalled until a new operating system was released.

---

