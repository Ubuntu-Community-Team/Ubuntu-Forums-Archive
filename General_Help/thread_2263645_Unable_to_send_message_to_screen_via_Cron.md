---
title: "Unable to send message to screen via Cron"
date: 2015-02-02
forum: General Help
---

### Post by kieran6 on 2015-02-02
Hi there

I have a simple script, that sends a message to a running screen like so:
```
sudo -u <user> screen -S <screen> -X stuff "message goes here"
```

When I run this for example, by calling ./script.sh it works 100% as intended and will send a message to the screen.

However, when I add the following to crontab:
```
* * * * * sh /home/<user>/script.sh
```

Nothing happens after many minutes (this should run once per minute.)
So to make sure the script was being run at all, I added this to the file:
```
sudo -u <user> screen -S <screen> -X stuff "message goes here"
touch test.txt
```

Now this file "test.txt" was being created as it should, but the input from stuff was still not being sent to screen.

All I can think of is that perhaps it isn't possible to use the screen -X stuff command from cron.
Does anyone know how to fix this, or perhaps a workaround that will work from cron?

Thank you for your time.

---

### Post by nerdtron on 2015-02-02
First try running the script the way cron will run it.

sh /home/<user>/script.sh

If that did not, something is wrong on the shell env....If so, this will probably work.

/bin/bash /home/<user>/script.sh

If that did work, then modify your cron entry.

---

### Post by buzzingrobot on 2015-02-02
You might need to set/export the DISPLAY environment variable correctly within the crontab entry.

Here's a look at how I did it in a crontab entry that calls a shell script:
```
*/9 * * * * export DISPLAY=:0; source ~/.Xdbus; /home/......../bin/scripts/offlineimapdaemon.sh &> /dev/null
```

This sets it to 0, which is very likely correct if you have a single display.

---

### Post by ajgreeny on 2015-02-02
I don't think I've ever tried to run a script that needs root permissions, ie, one needing sudo, with my user cron; can it even be done?

---

### Post by ian-weisser on 2015-02-02
It's possible to use cron to send commands to the 'screen' application.

However, it's most unwise to use sudo in a cron script. Better practice is to run the cronjob as the correct user.
If the other user is a human with a login and a /home dir, put it in their user-level crontab.
If the other user a system user, add a whole new crontab file to /etc/cron.d. Root crontabs have an extra field for the user for exactly this purpose.

---

### Post by kieran6 on 2015-02-03
> **nerdtron said:**
> First try running the script the way cron will run it.

sh /home/<user>/script.sh

If that did not, something is wrong on the shell env....If so, this will probably work.

/bin/bash /home/<user>/script.sh

If that did work, then modify your cron entry.

Both of those methods worked from the shell but neither worked from the crontab. Thank you for your input though.

> **buzzingrobot said:**
> You might need to set/export the DISPLAY environment variable correctly within the crontab entry.

Here's a look at how I did it in a crontab entry that calls a shell script:
```
*/9 * * * * export DISPLAY=:0; source ~/.Xdbus; /home/......../bin/scripts/offlineimapdaemon.sh &> /dev/null
```

This sets it to 0, which is very likely correct if you have a single display.

I gave that a try but no luck unfortunately. Thank you for your time though.

> **ajgreeny said:**
> I don't think I've ever tried to run a script that needs root permissions, ie, one needing sudo, with my user cron; can it even be done?

It can be done. The entire script runs fine it was just the screen command I was using that wasn't giving the desired result. Everything else in the script executed perfectly though.

> **ian-weisser said:**
> It's possible to use cron to send commands to the 'screen' application.

However, it's most unwise to use sudo in a cron script. Better practice is to run the cronjob as the correct user.
If the other user is a human with a login and a /home dir, put it in their user-level crontab.
If the other user a system user, add a whole new crontab file to /etc/cron.d. Root crontabs have an extra field for the user for exactly this purpose.

I'm very grateful to you, you're a very helpful person and I hope you know it's greatly appreciated. After one search I discovered that "sudo crontab -u server -e" would give me a crontab for the user responsible for the screen, and placing the script in that crontab made it work to perfection, and it's much safer than using the root one too. Thank you very much for your help.

---

