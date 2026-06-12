---
title: "WARNING Running Pipelight as Root warning. What to do?"
date: 2014-09-01
forum: General Help
---

### Post by benawhile on 2014-09-01
Hi. In June I did fresh install of Ubuntu 14.04 Windows XP dual boot.
Had to use the Gnome metacity desktop, Unity and Gnome compiz were too slow. My graphics chipset is 7 yrs old. VIA K8M890CE.

In order to watch some online videos, specifically C4OD, (UK Channel 4 On Demand) I had to get hal

    sudo add-apt-repository ppa:mjblenner/ppa-hal

    sudo apt-get update && sudo apt-get install hal

The resolution of videos was poor (jerky picture) so I tried installing pipelight like this:

```
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin &#8211;update
```

This made no difference to video resolution. Jerky picture still.
Videos are not watchable on full screen, but I can live with that for now. The problem is I keep getting warnings about pipelight, like this below, when all I was doing was running recently downloaded Ubuntu Tweaks from the terminal. I am uneasy about this pipelight, I don't know what it is, should I get rid of it and how? I was going to clean out my system with Tweak and Bleachbit but don't want to do anything now untill I understand this warning.

```
ben@ben-MS-7253:~$ sudo ubuntu-tweak
[sudo] password for ben: 
compizconfig - Info: Backend     : ini
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
[PIPELIGHT:LIN:unknown] attached to process.
[PIPELIGHT:LIN:unknown] checking environment variable PIPELIGHT_FLASH_CONFIG.
[PIPELIGHT:LIN:unknown] searching for config file pipelight-flash.
[PIPELIGHT:LIN:unknown] trying to load config file from '/home/ben/.config/pipelight-flash'.
[PIPELIGHT:LIN:unknown] trying to load config file from '/etc/pipelight-flash'.
[PIPELIGHT:LIN:unknown] trying to load config file from '/usr/share/pipelight/configs/pipelight-flash'.
[PIPELIGHT:LIN:unknown] sandbox not found or not installed!
[PIPELIGHT:LIN:flash] using wine prefix directory /home/ben/.wine-pipelight.
[PIPELIGHT:LIN:flash] checking plugin installation - this might take some time.
[PIPELIGHT:LIN:flash] -------------------------------------------------------
[PIPELIGHT:LIN:flash] WARNING! YOU ARE RUNNING THIS PIPELIGHT PLUGIN AS ROOT!
[PIPELIGHT:LIN:flash] THIS IS USUALLY NOT A GOOD IDEA! YOU HAVE BEEN WARNED!
[PIPELIGHT:LIN:flash] -------------------------------------------------------
[install-dependency] wine-flash-installer is already installed in '/home/ben/.wine-pipelight'.
[PIPELIGHT:LIN:flash] -------------------------------------------------------
[PIPELIGHT:LIN:flash] WARNING! YOU ARE RUNNING THIS PIPELIGHT PLUGIN AS ROOT!
[PIPELIGHT:LIN:flash] THIS IS USUALLY NOT A GOOD IDEA! YOU HAVE BEEN WARNED!
[PIPELIGHT:LIN:flash] -------------------------------------------------------
wine: /home/ben/.wine-pipelight is not owned by you
[PIPELIGHT:LIN:flash] ../common/common.c:168:receiveCommand(): unable to receive data.
[PIPELIGHT:LIN:flash] basicplugin.c:121:attach(): error during the initialization of the wine process - aborting.
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

---

### Post by claracc on 2014-09-02
In order to delete the pipelight plugin ( you don't install software without knowing what it is for: [https://wiki.archlinux.org/index.php/Pipelight](https://wiki.archlinux.org/index.php/Pipelight)), first you have to disable and remove the ppa repository you have used from your software sources.

The easiest way is through gui: open update manager and click on settings, in the window appearing click on other software tab, there you click on the ppa you want to disable, close (also you can remove the ppa if you want to get rid of it completely). See attached image

Then in a xterm (ctrl+alt+t) you can run the command to get rid of pipelight and its configuration files if any:

```
sudo apt-get --purge remove pipelight
```

Then you can run ```
sudo apt-get autoremove
``` to delete not more needed packages.

To know more about pipelight: [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)

---

### Post by SeijiSensei on 2014-09-02
You are getting that warning because you are running ubuntu-tweak as root, and it apparently talks to pipelight for some reason. So the pipelight invocation also happens with root privileges.

Pipelight is a solution for sites that use MS Silverlight like Netflix.  Sites like Amazon Instant and LoveFilm use DRM features in Adobe Flash.  Hal seems to help for those sites, but not the Silverlight ones, and vice versa for pipelight.

---

### Post by benawhile on 2014-09-02
Thank you to both.
I perhaps overstated my lack of knowledge of pipelight. I did at least know why I was installing it. As Seiji implies, it may be useful in future so I may keep it.
Presumably if I could run ubuntu tweak as user there would be no problem. But I can't yet run ubuntu tweak as user, and I can't find it in applications or system settings. Only terminal seems to work but I get this when I try to run as user:

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

Can anyone say here why I don't have an icon to run ubuntu tweaks or why I can't run it as user, or why i get the warning? If not I realise it has now become a ubuntu tweak problem and I will need a new post. Thank you claracc for the extremely helpful uninstall instructions. I will be more wary of ppa software in future as I didn't realise the risks of ppa for newbies.

---

