---
title: "gnome-terminal-server breaks with UTF8 locale claiming to be non-UTF8"
date: 2018-08-06
forum: General Help
---

### Post by alicia4542 on 2018-08-06
After using **Ubuntu 18.04** with lightdm for a month, I rebooted my laptop yesterday, and suddenly some Gnome software is not working.

In particular "gnome-terminal" which fails with this error:[COLOR=#b22222]

[/COLOR][INDENT][COLOR=#b22222]Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: Timeout was reached[/COLOR]
[/INDENT]

And in syslog, I find this:
[INDENT]systemd: Starting GNOME Terminal Server...
gnome-terminal-server: Non UTF-8 locale (ANSI_X3.4-1968) is not supported!
systemd: gnome-terminal-server.service: Main process exited, code=exited, status=8/n/a
systemd: gnome-terminal-server.service: Failed with result 'exit-code'.
systemd: Failed to start GNOME Terminal Server.
[/INDENT]

Note that I do not have any non-UTF8 locale:
[INDENT]> **locale -v**
LANG=en_CA.UTF-8
LANGUAGE=en_CA:en_GB:en_AU:en
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=en_CA.UTF-8

> **cat /etc/default/locale**
LANG=en_CA.UTF-8
LC_ALL=en_CA.UTF-8
LC_ADDRESS=en_CA.UTF-8                                                          
LC_IDENTIFICATION=en_CA.UTF-8                                                   
LC_MEASUREMENT=en_CA.UTF-8                                                      
LC_MONETARY=en_CA.UTF-8
LC_NAME=en_CA.UTF-8
LC_NUMERIC=en_CA.UTF-8
LC_PAPER=en_CA.UTF-8
LC_TELEPHONE=en_CA.UTF-8
LC_TIME=en_CA.UTF-8
LC_CTYPE=en_CA.UTF-8
LC_COLLATE=en_CA.UTF-8
LC_MESSAGES=en_CA.UTF-8

> **diff -s /etc/default/locale /etc/locale.conf**
Files /etc/default/locale and /etc/locale.conf are identical

# **locale-gen** 
Generating locales (this might take a while)...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IL.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
  ja_JP.UTF-8... done
  pt_BR.UTF-8... done
  pt_PT.UTF-8... done
Generation complete.
[/INDENT]

And I have reconfigured locales many times using "**locale-gen**" & "**dpkg-reconfigure locales**", and rebooting, without any luck.

Any advice, I am stuck on this without any solution and still get the same error.  "lightdm" is also no longer showing time & date on my unity menu bar like it did previously.

Thank you in advance.
Alicia.

---

