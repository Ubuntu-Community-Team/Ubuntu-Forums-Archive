---
title: "rkhunter update errors"
date: 2018-01-05
forum: General Help
---

### Post by lance bermudez on 2018-01-05
Can some body explain to me what is going on? Why update failed and the mirrors file has no required mirrors in it: /var/lib/rkhunter/db/mirrors.dat

update command error update failed
```

# rkhunter --update
[ Rootkit Hunter version 1.4.4 ]

Checking rkhunter data files...
  Checking file mirrors.dat                                  [ Skipped ]
  Checking file programs_bad.dat                             [ Update failed ]
  Checking file backdoorports.dat                            [ Update failed ]
  Checking file suspscan.dat                                 [ Update failed ]
  Checking file i18n versions                                [ Update failed ]

Please check the log file (/var/log/rkhunter.log)

```

/var/log/rkhunter.log
```

[08:38:06] Running Rootkit Hunter version 1.4.4 on Type40Tardis
[08:38:06]
[08:38:06] Info: Start date is Fri Jan  5 08:38:06 MST 2018
[08:38:06]
[08:38:06] Checking configuration file and command-line options...
[08:38:06] Info: Detected operating system is 'Linux'
[08:38:06] Info: Found O/S name: Ubuntu 16.04.3 LTS
[08:38:06] Info: Command line is /usr/bin/rkhunter --update
[08:38:06] Info: Environment shell is /bin/bash; rkhunter is using dash
[08:38:06] Info: Using configuration file '/etc/rkhunter.conf'
[08:38:06] Info: Installation directory is '/usr'
[08:38:06] Info: Using language 'en'
[08:38:06] Info: Using '/var/lib/rkhunter/db' as the database directory
[08:38:06] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[08:38:06] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin' as the command directories
[08:38:06] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[08:38:06] Info: X will be automatically detected
[08:38:06] Info: Using second color set
[08:38:06] Info: Found the 'basename' command: /usr/bin/basename
[08:38:06] Info: Found the 'diff' command: /usr/bin/diff
[08:38:06] Info: Found the 'dirname' command: /usr/bin/dirname
[08:38:06] Info: Found the 'file' command: /usr/bin/file
[08:38:06] Info: Found the 'find' command: /usr/bin/find
[08:38:06] Info: Found the 'ifconfig' command: /sbin/ifconfig
[08:38:06] Info: Found the 'ip' command: /sbin/ip
[08:38:06] Info: Found the 'ipcs' command: /usr/bin/ipcs
[08:38:06] Info: Found the 'ldd' command: /usr/bin/ldd
[08:38:06] Info: Found the 'lsattr' command: /usr/bin/lsattr
[08:38:06] Info: Found the 'lsmod' command: /sbin/lsmod
[08:38:06] Info: Found the 'lsof' command: /usr/bin/lsof
[08:38:06] Info: Found the 'mktemp' command: /bin/mktemp
[08:38:06] Info: Found the 'netstat' command: /bin/netstat
[08:38:06] Info: Found the 'perl' command: /usr/bin/perl
[08:38:06] Info: Found the 'pgrep' command: /usr/bin/pgrep
[08:38:06] Info: Found the 'ps' command: /bin/ps
[08:38:06] Info: Found the 'pwd' command: /bin/pwd
[08:38:06] Info: Found the 'readlink' command: /bin/readlink
[08:38:06] Info: Found the 'stat' command: /usr/bin/stat
[08:38:06] Info: Found the 'strings' command: /usr/bin/strings
[08:38:06] Info: Found the 'wget' command: /usr/bin/wget
[08:38:06] Info: The mirrors file will be rotated
[08:38:06] Info: Only local mirrors will be used
[08:38:06] Info: The mirrors file will not be updated
[08:38:06] Info: Logging to log file: /var/log/rkhunter.log
[08:38:06] Info: Locking is not being used
[08:38:06]
[08:38:06] Checking rkhunter data files...
[08:38:06] Info: Created temporary file '/var/lib/rkhunter/tmp/rkhunter.upd.nZdbuPliDR'
[08:38:06] Checking file mirrors.dat                         [ Skipped ]
[08:38:07] Info: The mirrors file has no required mirrors in it: /var/lib/rkhunter/db/mirrors.dat
[08:38:07] Warning: Download of 'programs_bad.dat' failed: Unable to determine the latest version number.
[08:38:07] Checking file programs_bad.dat                    [ Update failed ]
[08:38:07] Info: The mirrors file has no required mirrors in it: /var/lib/rkhunter/db/mirrors.dat
[08:38:07] Warning: Download of 'backdoorports.dat' failed: Unable to determine the latest version number.
[08:38:07] Checking file backdoorports.dat                   [ Update failed ]
[08:38:07] Info: The mirrors file has no required mirrors in it: /var/lib/rkhunter/db/mirrors.dat
[08:38:07] Warning: Download of 'suspscan.dat' failed: Unable to determine the latest version number.
[08:38:07] Checking file suspscan.dat                        [ Update failed ]
[08:38:07] Info: The mirrors file has no required mirrors in it: /var/lib/rkhunter/db/mirrors.dat
[08:38:07] Checking file i18n versions                       [ Update failed ]
[08:38:07] Warning: Download of 'i18n.ver' failed: Unable to determine the latest version number.
[08:38:07]
[08:38:07] Info: End date is Fri Jan  5 08:38:07 MST 2018

```

---

### Post by #&amp;thj^% on 2018-01-05
It appears that sourceforge.net website is temporarily in static offline mode.
Only a very limited set of project pages are available until the main website returns online.
this has been going on just recently (Since July 2017) no clue why. 
Found a couple of links that may give us a clue: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=765895](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=765895)
And: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=869760](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=869760)
FWIW:Not seeing this on non-debian installs
```
rkhunter --update
[ Rootkit Hunter version 1.4.4 ]

Checking rkhunter data files...
  Checking file mirrors.dat                                  [ No update ]
  Checking file programs_bad.dat                             [ No update ]
  Checking file backdoorports.dat                            [ No update ]
  Checking file suspscan.dat                                 [ No update ]
  Checking file i18n/cn                                      [ No update ]
  Checking file i18n/de                                      [ No update ]
  Checking file i18n/en                                      [ Updated ]
  Checking file i18n/tr                                      [ Updated ]
  Checking file i18n/tr.utf8                                 [ Updated ]
  Checking file i18n/zh                                      [ No update ]
  Checking file i18n/zh.utf8                                 [ No update ]
  Checking file i18n/ja                                      [ No update ]

```
Sorry wish I better news.

---

### Post by HermanAB on 2018-01-06
Note that the rkhunter program doesn't really do anything useful.  The only thing it is good at, is raising false alarms, so don't waste your time.  

Rather get your Meltdown and Spectre security patches installed and forget about rkhunter.

---

