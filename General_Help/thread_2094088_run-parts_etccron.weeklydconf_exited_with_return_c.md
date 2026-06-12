---
title: "run-parts: /etc/cron.weekly/dconf exited with return code 1"
date: 2012-12-12
forum: General Help
---

### Post by zasran on 2012-12-12
I keep getting email from cron (Ubuntu quantal):

--------------------- begin quote ---------------------
/etc/cron.weekly/dconf:
error: no command specified

Usage:
  dconf COMMAND [ARGS...]

Commands:
  help              Show this information
  read              Read the value of a key
  list              List the contents of a dir
  write             Change the value of a key
  reset             Reset the value of a key or dir
  update            Update the system databases
  watch             Watch a path for changes
  dump              Dump an entire subpath to stdout
  load              Populate a subpath from stdin

Use 'dconf help COMMAND' to get detailed help.

run-parts: /etc/cron.weekly/dconf exited with return code 1

--------------------- end quote ---------------------

  any ideas what's supposed to happen? File /etc/cron.weekly/dconf is a link to /usr/bin/dconf (installed by dconf-tools). When I run it without any arguments it prints the same message I get from cron. Any ideas how it should be set up? Tried to reconfigure dconf-tools but it didn't help...

  Can't find who is supposed to create /etc/cron.weekly/dconf, I assume it's dynamically created by some post install script (apt-file or dpkg -S don't find it),

  Relevant packages:

erik@jojda:~$ dpkg -l dconf\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version             Architecture        Description
+++-=============================-===================-===================-===============================================================
rc  dconf                         0.5.1-2             all                 collect system information
ii  dconf-gsettings-backend:amd64 0.14.1-0ubuntu0.1   amd64               simple configuration storage system - GSettings back-end
ii  dconf-service                 0.14.1-0ubuntu0.1   amd64               simple configuration storage system - D-Bus service
ii  dconf-tools                   0.14.1-0ubuntu0.1   amd64               simple configuration storage system - utilities

  thanks,

        erik

---

