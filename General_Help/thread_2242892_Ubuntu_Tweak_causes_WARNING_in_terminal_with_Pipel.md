---
title: "Ubuntu Tweak causes WARNING in terminal with Pipelight"
date: 2014-09-04
forum: General Help
---

### Post by benawhile on 2014-09-04
I have Ubuntu 14.04,  gnome metacity desktop
I Installed 0.8.7 current version of Ubuntu Tweak using the deb package and opening it with Ubuntu Software Centre.
I could find no icon to start program in system settings or applications, so I ran in terminal and got this warning:

```

 ben@ben-MS-7253:~$ sudo ubuntu-tweak
[sudo] password for ben:
compizconfig – Info: Backend     : ini
compizconfig – Info: Integration : true
compizconfig – Info: Profile     : default
[PIPELIGHT:LIN:unknown] attached to process.
[PIPELIGHT:LIN:unknown] checking environment variable PIPELIGHT_FLASH_CONFIG.
[PIPELIGHT:LIN:unknown] searching for config file pipelight-flash.
[PIPELIGHT:LIN:unknown] trying to load config file from ‘/home/ben/.config/pipelight-flash’.
[PIPELIGHT:LIN:unknown] trying to load config file from ‘/etc/pipelight-flash’.
[PIPELIGHT:LIN:unknown] trying to load config file from ‘/usr/share/pipelight/configs/pipelight-flash’.
[PIPELIGHT:LIN:unknown] sandbox not found or not installed!
[PIPELIGHT:LIN:flash] using wine prefix directory /home/ben/.wine-pipelight.
[PIPELIGHT:LIN:flash] checking plugin installation – this might take some time.
[PIPELIGHT:LIN:flash] ——————————————————-
[PIPELIGHT:LIN:flash] WARNING! YOU ARE RUNNING THIS PIPELIGHT PLUGIN AS ROOT!
[PIPELIGHT:LIN:flash] THIS IS USUALLY NOT A GOOD IDEA! YOU HAVE BEEN WARNED!
[PIPELIGHT:LIN:flash] ——————————————————-
[install-dependency] wine-flash-installer is already installed in ‘/home/ben/.wine-pipelight’.
[PIPELIGHT:LIN:flash] ——————————————————-
[PIPELIGHT:LIN:flash] WARNING! YOU ARE RUNNING THIS PIPELIGHT PLUGIN AS ROOT!
[PIPELIGHT:LIN:flash] THIS IS USUALLY NOT A GOOD IDEA! YOU HAVE BEEN WARNED!
[PIPELIGHT:LIN:flash] ——————————————————-
wine: /home/ben/.wine-pipelight is not owned by you
[PIPELIGHT:LIN:flash] ../common/common.c:168:receiveCommand(): unable to receive data.
[PIPELIGHT:LIN:flash] basicplugin.c:121:attach(): error during the initialization of the wine process – aborting.
[PIPELIGHT:LIN:flash] using thread asynccall event handling.
No bp log location saved, using default.
[000:000] Cpu: 15.107.1, x2, 2099Mhz, 1888MB
[000:000] Computer model: Not available
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is Gtk2.
[000:026] Using Gtk2 toolkit
No bp log location saved, using default.
[000:000] Cpu: 15.107.1, x2, 2099Mhz, 1888MB
[000:001] Computer model: Not available
[000:103] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:103] No bp log location saved, using default.
[000:104] Cpu: 15.107.1, x2, 2099Mhz, 1888MB
[000:104] Computer model: Not available
[000:104] Browser XEmbed support present: 1
[000:104] Browser toolkit is Gtk2.
[000:104] Using Gtk2 toolkit
[000:430] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:430] No bp log location saved, using default.
[000:431] Cpu: 15.107.1, x2, 2099Mhz, 1888MB
[000:431] Computer model: Not available

```

 The main ubuntu tweak window opened OK but I closed it because of the warning.

So how can I run ubuntu Tweak safely or do I have to uninstall pipelight? It won’t run at all without the sudo command.

---

### Post by yancek on 2014-09-04
What exactly are you trying to accomplish with Ubuntu Tweak?  As the warning indicates, the pipelight-plugin does not need to be run by root but you haven't told us what your intentions or end goals are.  I think part of whatever problem you have is in the output below from your post:

> wine: /home/ben/.wine-pipelight is not owned by you

You should check who the owner is.

---

### Post by benawhile on 2014-09-04
I want Ubuntu tweak so I can use the clean up facility (tweak janitor?) Ubuntu OS is taking up more and more space, it has grown from 3GB to 6GB.
As for checking who the owner is, please would you tell me how to find that out and what I should do about it? I am the only person that uses this computer.
Did I have to install wine when I installed pipelight?

The problem is, so, pipelight doesn't need to be run by root, but I didn't want to run ubuntu tweak as root in the first place, let alone did I want it to invoke wine and pipelight. OK if it has to invoke wine and pipelight to clean them up so be it. I have a problem. I would be quite happy to run as user, but it won't run for user, sudo is the only way it would run. It looks like a vicious circle to me so far.;)

---

### Post by benawhile on 2014-09-05
More info: I installed pipelight a few weeks ago like this:


```
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin –update

```

When I try to run ubuntu tweak withour the sudo I get this

```
ben@ben-MS-7253:~$ ubuntu-tweak
Traceback (most recent call last):
  File "/usr/bin/ubuntu-tweak", line 73, in <module>
    class UbuntuTweakApp(Gtk.Application):
  File "/usr/bin/ubuntu-tweak", line 75, in UbuntuTweakApp
    log = logging.getLogger('Launcher')
  File "/usr/lib/python2.7/logging/__init__.py", line 1559, in getLogger
    return Logger.manager.getLogger(name)
  File "/usr/lib/python2.7/logging/__init__.py", line 1038, in getLogger
    rv = (self.loggerClass or _loggerClass)(name)
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/common/debug.py", line 155, in __init__
    TweakLogger.LOG_FILE_HANDLER = logging.FileHandler(filename, 'w')
  File "/usr/lib/python2.7/logging/__init__.py", line 903, in __init__
    StreamHandler.__init__(self, self._open())
  File "/usr/lib/python2.7/logging/__init__.py", line 928, in _open
    stream = open(self.baseFilename, self.mode)
IOError: [Errno 13] Permission denied: '/home/ben/.config/ubuntu-tweak/ubuntu-tweak.log'
ben@ben-MS-7253:~$ 

```

---

