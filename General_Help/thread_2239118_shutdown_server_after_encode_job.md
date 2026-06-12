---
title: "shutdown server after encode job"
date: 2014-08-12
forum: General Help
---

### Post by Marcel_van_Leeuwen on 2014-08-12
I have script to encode some files in a directory with HandBrakeCLI. At the end of this script the server shutdown with "shutdown -h 0" To do this the script must be run as root is there a other way?

---

### Post by JetStorm on 2014-08-12
If you're starting the script manually every time you can just try adding sudo in front of the script name. 
For example:
sudo script.sh

If you're starting it from a cron job you could try adding the user you're starting it from to the shutdown group (which you'll also have to create).
There are detailed instructions over here:
[http://ubuntuforums.org/showthread.php?t=134968](http://ubuntuforums.org/showthread.php?t=134968)

---

### Post by SeijiSensei on 2014-08-12
Another option is to have the encoding script create a "semaphore" file when it completes. 
```
touch /tmp/done-encoding
```
You can then run a script periodically from /etc/crontab with root permissions that looks for that file and shuts down the computer if it exists.  
```

#!/bin/sh
if [ -f /tmp/done-encoding ] 
then
    rm -f /tmp/done-encoding
    /sbin/shutdown now
fi

```

---

