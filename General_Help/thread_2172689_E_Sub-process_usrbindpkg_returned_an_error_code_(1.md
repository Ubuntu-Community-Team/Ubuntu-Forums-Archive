---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-09-06
forum: General Help
---

### Post by palashchatterjee01 on 2013-09-06
I get the following error while trying to use apt-get install -f. Please help
```

dpkg: dependency problems prevent configuration of usb-modeswitch: usb-modeswitch-data (20120120-0ubuntu1) breaks usb-modeswitch (<< 1.1.9) and is installed.
  Version of usb-modeswitch to be configured is 0.9.7.
dpkg: error processing usb-modeswitch (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 usb-modeswitch
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Executing apt-get remove --purge usb-modeswitch gives another error.
```

The following packages have unmet dependencies:
 vodafone-mobile-connect : Depends: usb-modeswitch (>= 0.9.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by varunendra on 2013-09-06
Welcome to the forums Palash !

What happens if you try to purge both offending packages at once :
```
sudo apt-get purge vodafone-mobile-connect usb-modeswitch
```

By the way, how did you initiate the installation? Through apt-get or dpkg or some other way?
Were there any other related packages installed prior to this error?

Just curious, because usually these USB modem application packages come as source code, not as .deb files.

---

