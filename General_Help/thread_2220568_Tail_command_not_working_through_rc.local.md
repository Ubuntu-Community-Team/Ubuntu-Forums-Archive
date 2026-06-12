---
title: "Tail command not working through rc.local"
date: 2014-04-28
forum: General Help
---

### Post by DappereDodo on 2014-04-28
Hi all,

To combat a driver bug in my Terratec Cinergy HD DVB-C card I want to run the following script:

```
#!/bin/bash

tail -F /var/log/syslog | grep --line-buffered "Transport error indicator" | while read line
do
  service tvheadend stop
  sudo modprobe -r mantis
  sudo modprobe -r tda10021
  sudo modprobe tda10021
  sudo modprobe mantis
  service tvheadend start
  mail -s "Mantis driver restarted" someone@some.where
done
```

This script works fine when run from a terminal window, but if I add it to rc.local it doesn't. The content of rc.local is:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sh /root/automantis.sh &

exit 0

```

I know the script is running, because ps aux | grep mantis shows this:
```
root      3284  0.0  0.0   3356   272 ?        S    Apr24   0:00 /bin/bash /root/automantis.sh
root      3290  0.0  0.0   3356   308 ?        S    Apr24   0:00 /bin/bash /root/automantis.sh
```

So the script is running, but the commands between do and done are not executed when the "transport error indicator" lines start appearing in syslog. Does anyone know what the problem might be? I'm running Ubuntu 12.04 (via an upgrade from 10.04)

---

