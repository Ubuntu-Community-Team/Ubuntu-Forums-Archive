---
title: "Call of duty 2 Fail2ban regex error."
date: 2024-07-25
forum: General Help
---

### Post by geeb21 on 2024-07-25
[COLOR=#222222][FONT=Verdana]Hello.[/FONT][/COLOR][COLOR=#222222][FONT=Verdana] [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]I would be so worried about having a logo.[/FONT][/COLOR][COLOR=#222222][FONT=Verdana] [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]I want to filter out cheaters on a server. [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]Fail2ban - jail + filter - iptables.

/etc/fail2ban/jail.d/cod2.conf
[cod2]
enabled = true
port = 28960
protocol = udp
filter = cod2
logpath = /home/cod2server/log/console/cod2server-console.log
maxretry = 3
findtime = 600
bantime = 3600
action = iptables-multiport[name=cod2, port="28960", protocol=udp, chain=INPUT
]

Regexben:
/etc/fail2ban/filter.d/cod2.conf


[Definition]
failregex = Rcon from <HOST>:.*
ignoreregex =



Terminal:


sudo fail2ban-regex /log/console/cod2server-console.log /etc/fail2ban/filter.d/cod2.conf

Running tests
=============

Use   failregex filter file : cod2, basedir: /etc/fail2ban
Use         log file : /home/cod2server/log/console/cod2server-console.log
Use         encoding : UTF-8

Traceback (most recent call last):
  File "/usr/bin/fail2ban-regex", line 34, in <module>
    exec_command_line()
  File "/usr/lib/python3/dist-packages/fail2ban/client/fail2banregex.py", line 836, in exec_command_line
    if not fail2banRegex.start(args):
  File "/usr/lib/python3/dist-packages/fail2ban/client/fail2banregex.py", line 776, in start
    self.process(test_lines)
  File "/usr/lib/python3/dist-packages/fail2ban/client/fail2banregex.py", line 584, in process
    line_datetimestripped, ret, is_ignored = self.testRegex(line)
  File "/usr/lib/python3/dist-packages/fail2ban/client/fail2banregex.py", line 456, in testRegex
    found = self._filter.processLine(line, date)
  File "/usr/lib/python3/dist-packages/fail2ban/server/filter.py", line 613, in processLine
    timeMatch = self.dateDetector.matchTime(line)
  File "/usr/lib/python3/dist-packages/fail2ban/server/datedetector.py", line 368, in matchTime
    (line[distance] == self.__lastPos[2] and not self.__lastPos[2].isalnum())
IndexError: string index out of range


Thanks help.[/FONT][/COLOR]

---

### Post by currentshaft on 2024-07-25
Which version of Ubuntu, Python and fail2ban? Also post the log file here, since that is causing the error.

---

### Post by geeb21 on 2024-07-25
But everything else works in fail2ban. Email ssh protection.

Ubuntu 18.04
Python 3.8.16

fail2ban-client version
0.11.2


 sudo fail2ban-regex /home/cod2server/log/console/cod2server-console.log /etc/fail2ban/filter.d/cod2.conf



Running tests
=============

Use   failregex filter file : cod2, basedir: /etc/fail2ban
Use         log file : /home/cod2server/log/console/cod2server-console.log
Use         encoding : UTF-8

Traceback (most recent call last):
  File "/usr/bin/fail2ban-regex", line 34, in <module>
    exec_command_line()
  File "/usr/lib/python3/dist-packages/fail2ban/client/fail2banregex.py", line 836, in exec_command_line
    if not fail2banRegex.start(args):
  File "/usr/lib/python3/dist-packages/fail2ban/client/fail2banregex.py", line 776, in start
    self.process(test_lines)
  File "/usr/lib/python3/dist-packages/fail2ban/client/fail2banregex.py", line 584, in process
    line_datetimestripped, ret, is_ignored = self.testRegex(line)
  File "/usr/lib/python3/dist-packages/fail2ban/client/fail2banregex.py", line 456, in testRegex
    found = self._filter.processLine(line, date)
  File "/usr/lib/python3/dist-packages/fail2ban/server/filter.py", line 613, in processLine
    timeMatch = self.dateDetector.matchTime(line)
  File "/usr/lib/python3/dist-packages/fail2ban/server/datedetector.py", line 368, in matchTime
    (line[distance] == self.__lastPos[2] and not self.__lastPos[2].isalnum())
IndexError: string index out of range

---

### Post by currentshaft on 2024-07-25
You need to post the log as requested if you expect help.

---

### Post by geeb21 on 2024-07-26
The error is not present in the fail2 log.
I add an ip address manually, the ip is blocked in the given section. But the game cannot read the appropriate information from the log section.

python debug
Error processing line 1 of /usr/lib/python3/dist-packages/zope.component-4.3.0-nspkg.pth:

Fatal Python error: init_import_size: Failed to import the site module
Python runtime state: initialized
Traceback (most recent call last):
  File "/usr/lib/python3.8/site.py", line 175, in addpackage
    exec(line)
  File "<string>", line 1, in <module>
  File "/usr/lib/python3.8/importlib/util.py", line 14, in <module>
    from contextlib import contextmanager
  File "/usr/lib/python3.8/contextlib.py", line 5, in <module>
    from collections import deque
  File "/usr/lib/python3.8/collections/__init__.py", line 28, in <module>
    from collections.abc import Mapping
  File "/usr/lib/python3.8/collections/abc.py", line 1, in <module>
    from collections.abc import Mapping
ImportError: cannot import name 'Mapping' from partially initialized module 'collections.abc' (most likely due to a circular import) (/usr/lib/python3.8/collections/abc.py)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3.8/site.py", line 597, in <module>
    main()
  File "/usr/lib/python3.8/site.py", line 584, in main
    known_paths = addsitepackages(known_paths)
  File "/usr/lib/python3.8/site.py", line 367, in addsitepackages
    addsitedir(sitedir, known_paths)
  File "/usr/lib/python3.8/site.py", line 214, in addsitedir
    addpackage(sitedir, name, known_paths)
  File "/usr/lib/python3.8/site.py", line 185, in addpackage
    import traceback
  File "/usr/lib/python3.8/traceback.py", line 3, in <module>
    import collections
  File "/usr/lib/python3.8/collections/__init__.py", line 28, in <module>
    from collections.abc import Mapping
  File "/usr/lib/python3.8/collections/abc.py", line 1, in <module>
    from collections.abc import Mapping
ImportError: cannot import name 'Mapping' from partially initialized module 'collections.abc' (most likely due to a circular import) (/usr/lib/python3.8/collections/abc.py)

---

### Post by currentshaft on 2024-07-26
You keep asking why the output of a program is a certain way without telling us the input. This is not a productive use of our time together.

---

### Post by geeb21 on 2024-07-26
it doesn't log in fail2 because there is nothing...

pattern in the log:

Rcon from 192.168.9.64:28960:
pb_sv_plist
Rcon from 192.168.9.64:28960:
pb_sv_plist
Rcon from 192.168.9.64:28960:
pb_sv_plist
Rcon from 192.168.9.64:28960:
pb_sv_plist
Rcon from 192.168.9.64:28960:
pb_sv_plist
Rcon from 192.168.9.64:28960:
pb_sv_plist

but I don't know how to write filter.d so that it bans after a certain number of attempts.
old counter strike fail2ban:

# Fail2Ban filter for failure attempts in Counter Strike-1.6
[Definition]
failregex = ^: Bad Rcon: "rcon \d+ "\S+"  sv_contact ".*?"" from "<HOST>:\d+"$
ignoreregex =
datepattern = ^L %%d/%%m/%%Y - %%H:%%M:%%S

jail.conf:
 [counter-strike] logpath = /opt/cstrike/logs/L[0-9]*.log tcpport = 27030,27031,27032,27033,27034,27035,27036,27037,27038,27039 udpport = 1200,27000,27001,27002,27003,27004,27005,27006,27007,27008,27009,27010,27011,27012,27013,27014,27015 action_  = %(default/action_)s[name=%(__name__)s-tcp, port="%(tcpport)s", protocol="tcp"]            %(default/action_)s[name=%(__name__)s-udp, port="%(udpport)s", protocol="udp"]

---

