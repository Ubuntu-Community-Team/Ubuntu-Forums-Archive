---
title: "hdparm config not started at booot 14.04"
date: 2014-09-21
forum: General Help
---

### Post by shag00 on 2014-09-21
I have been trying to change some drive parameters by using hdparm.conf but have had no luck. I can work with the command line without problems which tells that hdparm is working but the configuration file settings are not being applied so I began chasing down the config file and if I understand what is written, hdparm.conf should be initialised/read by /etc/init.d/hdparm (or similar) but such a file does not exist on my machine. I am not certain what releases of Ubuntu these threads relate to so I removed and re installed hdparm in the hope that whatever initialisation files etc would be installed automatically but alas that did not occur.

So can anyone confirm where /etc/hdparm.conf is read from.

---

### Post by shag00 on 2014-09-24
I have done a little more homework on this problem and I am really after confirmation of what I think is happening.

hdparm starts from   [COLOR=#008000]/lib/udev/rules.d/85-hdparm.rules[/COLOR]                            which calls
                            [COLOR=#008000]/lib/udev/hdparm [/COLOR]                                                 which references
                            [COLOR=#008000]/lib/hdparm/hdparm-functions[/COLOR]                                 which appears to ask for the configuration details with this line (1/3 of the way down the script)
                            [COLOR=#0000ff]egrep -v '^[[:space:]]*(#|$)'  /etc/hdparm.conf   |[/COLOR]   (which I think means import all lines not starting with # or blank lines)

However, in [COLOR=#008000]/lib/hdparm/hdparm-functions[/COLOR]  after the above egrep line there is a global settings section which seems to be overriding the egrep line, in relation to power management.

My machine is a desktop with no battery power.

Would really appreciate some direction from somebody who really understands how these scripts fit together. All I want to is have the hdparm.conf values used by the system.

---

