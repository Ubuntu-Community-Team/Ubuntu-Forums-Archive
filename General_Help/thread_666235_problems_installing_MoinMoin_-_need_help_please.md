---
title: "problems installing MoinMoin - need help please"
date: 2008-01-13
forum: General Help
---

### Post by tjk on 2008-01-13
I've spent hours trying to get the Desktop version of MoinMoin working and at times I seem to be close... but now I get the following message:[INDENT][SIZE=1]Loading ...[/SIZE]
[SIZE=1]MoinMoin - 1.6.0 [release][/SIZE]

[SIZE=1]035408 INFO     logging initialized[/SIZE]
[SIZE=1]035408 INFO     Serving on 127.0.0.1:8000[/SIZE]
[SIZE=1]035408 INFO     Running as uid/gid 33/33[/SIZE]
[SIZE=1]035419 INFO     127.0.0.1 "GET / HTTP/1.1" 500 -[/SIZE]
[SIZE=1]035419 ERROR    ConfigurationError:[/SIZE]
[SIZE=1]data_dir "/home/tim/Moin/wiki/data" does not exists, or has incorrect ownership or [/SIZE][SIZE=1]permissions.[/SIZE]

[SIZE=1]Make sure the directory and the subdirectory pages are owned by the web[/SIZE]
[SIZE=1]server and are readable, writable and executable by the web server user[/SIZE]
[SIZE=1]and group.[/SIZE]

[SIZE=1]It is recommended to use absolute paths and not relative paths. Check[/SIZE]
[SIZE=1]also the spelling of the directory name.[/SIZE]
[SIZE=1]Traceback (most recent call last):[/SIZE]
[SIZE=1]  File "/home/tim/Moin/MoinMoin/request/request_standalone.py", line 53, in __init__[/SIZE]
[SIZE=1]    RequestBase.__init__(self, properties)[/SIZE]
[SIZE=1]  File "/home/tim/Moin/MoinMoin/request/__init__.py", line 216, in __init__[/SIZE]
[SIZE=1]    self._load_multi_cfg()[/SIZE]
[SIZE=1]  File "/home/tim/Moin/MoinMoin/request/__init__.py", line 381, in _load_multi_cfg[/SIZE]
[SIZE=1]    self.cfg = multiconfig.getConfig(self.url)[/SIZE]
[SIZE=1]  File "/home/tim/Moin/MoinMoin/config/multiconfig.py", line 170, in getConfig[/SIZE]
[SIZE=1]    cfg = _makeConfig(cfgName)[/SIZE]
[SIZE=1]  File "/home/tim/Moin/MoinMoin/config/multiconfig.py", line 106, in _makeConfig[/SIZE]
[SIZE=1]    cfg = configClass(name)[/SIZE]
[SIZE=1]  File "/home/tim/Moin/MoinMoin/config/multiconfig.py", line 712, in __init__[/SIZE]
[SIZE=1]    self._check_directories()[/SIZE]
[SIZE=1]  File "/home/tim/Moin/MoinMoin/config/multiconfig.py", line 924, in _check_directories[/SIZE]
[SIZE=1]    raise error.ConfigurationError(msg)[/SIZE]
[SIZE=1]ConfigurationError:[/SIZE]
[SIZE=1]data_dir "/home/tim/Moin/wiki/data" does not exists, or has incorrect ownership or[/SIZE]
[SIZE=1]permissions.[/SIZE]

[SIZE=1]Make sure the directory and the subdirectory pages are owned by the web[/SIZE]
[SIZE=1]server and are readable, writable and executable by the web server user[/SIZE]
[SIZE=1]and group.[/SIZE]

[SIZE=1]It is recommended to use absolute paths and not relative paths. Check[/SIZE]
[SIZE=1]also the spelling of the directory name.[/SIZE]
[/INDENT]Any ideas?

---

### Post by tjk on 2008-01-13
Anyone?

---

### Post by popch on 2008-01-13
The cue line appears to be

data_dir "/home/tim/Moin/wiki/data" does not exists, or has incorrect ownership or
permissions.

Make sure that the directory mentioned in the message does indeed exist. Do you start MoinMoin within your own user session (i.e. in a terminal by entering 'MoinMoin' or some such)? I have no access to MoinMoin documentation. Does the application need you to run some setup after installation?

---

### Post by tjk on 2008-01-13
> **popch said:**
> The cue line appears to be

data_dir "/home/tim/Moin/wiki/data" does not exists, or has incorrect ownership or
permissions.

Make sure that the directory mentioned in the message does indeed exist. Do you start MoinMoin within your own user session (i.e. in a terminal by entering 'MoinMoin' or some such)? I have no access to MoinMoin documentation. Does the application need you to run some setup after installation?

Yes, the directory exists.
I have tried using both root and user sessions.
There is a setup, but usually modifications/configurations are needed.. these are the instructions that I've been using: [http://moinmoin.wikiwikiweb.de/HelpOnInstalling/BasicInstallation](http://moinmoin.wikiwikiweb.de/HelpOnInstalling/BasicInstallation)

---

### Post by popch on 2008-01-13
Sorry, I don't know MoinMoin or Python enough to be of any help here.

---

