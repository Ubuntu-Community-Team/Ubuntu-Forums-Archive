---
title: "HDD clicking - how to make hdparm fix stick?"
date: 2015-11-15
forum: General Help
---

### Post by maglin2 on 2015-11-15
I have an Acer Aspire 7736Z laptop running Ubuntu 15.10 that suffers from HDD click.

I can fix the problem with:

[COLOR=#0000FF][COLOR=#0000FF]sudo hdparm -B 254 /dev/sda

[/COLOR][/COLOR]I can make this the default at startup by editing [COLOR=#0000FF]/etc/hdparm.conf [/COLOR]and adding

[B][COLOR=#0000FF]/dev/sda {
    apm = 254
    apm_battery = 254
}[/COLOR][/B]

(thanks to easy linux tips project).

The problem is that in neither case does the fix survive suspend/resume. After suspend I have hdparm -B = 128 again, and a clicking HDD.

Does anyone know of a way to make the hdparm change fix permanent, without disabling suspend?

Thanks

---

### Post by tgalati4 on 2015-11-15
Try putting your *hdparm* command in a resume script, without *sudo*, so it gets run every time the laptop resumes.  

Some reading:

[http://askubuntu.com/questions/92218/how-to-execute-a-command-after-resume-from-suspend](http://askubuntu.com/questions/92218/how-to-execute-a-command-after-resume-from-suspend)

[http://askubuntu.com/questions/250690/how-to-run-a-script-when-suspending-resuming-sony-vaio-ubuntu-12-04](http://askubuntu.com/questions/250690/how-to-run-a-script-when-suspending-resuming-sony-vaio-ubuntu-12-04)

Post the final version of your script, because it will take a few iterations to get it to work correctly.

---

### Post by maglin2 on 2015-11-15
Thanks for the links. I have never attempted to write a script before in my life, so this exercise may test your patience. 

My guess from looking at those examples and a few others would be something like this:
```
#!/bin/bash

case "$1" in
    resume)
        # Set hdparm -B to 254
    hdparm -B 254 /dev/sda
        ;;
esac
```

I would then make it executable - like this I believe:
sudo chmod a+x path/to/file.

The other question is where to put it. Up to 14.04 the correct place seems to have been /etc/pm/sleep.d.Since 15.04 I gather systemd has complicated matters. Some links seem to suggest putting scripts in lib/systemd/system-sleep. Others suggest putting a systemd service in there calling the script from somewhere else, and then enabling the systemd service.

Any help appreciated!

PS - I've spotted that there already is a linked script in /usr/lib/pm-utils/sleep.d that sets hdparm -B on resume (to 128 on battery) - so there is an interaction to consider.

---

### Post by pqwoerituytrueiwoq on 2015-11-15
i would disable that script or comment out that line so it cant set it to 128

---

### Post by tgalati4 on 2015-11-15
Your script should work fine.    I'm running 14.04 so I am blissfully ignorant of *systemd*.  The patience tested will be yours.

You can change the 95hdparm-apm script directly, just add some comments with your changes.  Back up the original script and put it in /old directory.  If you leave both scripts in the directory, they will both get executed.  Understand that any future system updates may overwrite your changes.

> tgalati4@Mint17 /usr/lib/pm-utils/sleep.d $ ls -la
total 72
drwxr-xr-x 2 root root  4096 Aug 12 08:54 .
drwxr-xr-x 7 root root  4096 Dec 19  2014 ..
-rwxr-xr-x 1 root root   292 Jul 15  2014 000kernel-change
-rwxr-xr-x 1 root root   274 Jul 15  2014 00logging
-rwxr-xr-x 1 root root   483 Jul 15  2014 00powersave
-rwxr-xr-x 1 root root   316 Jul 15  2014 50unload_alx
-rwxr-xr-x 1 root root   267 Jun 15 08:11 60_wpa_supplicant
-rwxr-xr-x 1 root root   453 Jul 15  2014 75modules
-rwxr-xr-x 1 root root   614 Jul 15  2014 90clock
-rwxr-xr-x 1 root root  1098 Jul 15  2014 94cpufreq
-rwxr-xr-x 1 root root   270 Feb 19  2014 95anacron
lrwxrwxrwx 1 root root    23 Dec 19  2014 **95hdparm-apm -> ../power.d/95hdparm-apm**
-rwxr-xr-x 1 root root   305 Jul 15  2014 95led
-rwxr-xr-x 1 root root 14075 Jul 15  2014 98video-quirk-db-handler
-rwxr-xr-x 1 root root  5850 Jul 15  2014 99video


---

### Post by maglin2 on 2015-11-15
Thanks for the help. I couldn't get my original attempt at a script to work no matter where I put it.

It wasn't clear to me how to modify the existing 95hdparm-apm script, since I couldn't find 128 in it anywhere - it may be a variable called from somewhere else I think

Much to my surprise, I believe I have now solved this problem adapting the advice given here:

[http://askubuntu.com/questions/661715/make-a-script-start-after-suspend-in-ubuntu-15-04-systemd](http://askubuntu.com/questions/661715/make-a-script-start-after-suspend-in-ubuntu-15-04-systemd)

My solution is a bit messy, involving two scripts, one /usr/local/bin/sethdparm
```
#!/bin/sh
hdparm -B 254 /dev/sda
```

and one /lib/systemd/system-sleep/00sethdparm

```
#!/bin/sh
if [ $1 = post ] && [ $2 = suspend ]
then /usr/local/bin/sethdparm
fi
```

I suspect I could simplify to a single systemd script, and when I get a chance I'll have a go.

Thanks again.

---

### Post by maglin2 on 2015-11-16
For anyone else having this problem it turns out that for me the only change needed to fix it in 15.10 was to add the following script to /lib/systemd/system-sleep. Call it something like 00sethdparm and make it executable.

```
#!/bin/sh
if [ $1 = post ]
then hdparm -B 254 /dev/sda
fi
```

There was no need to modify [COLOR=#0000FF]/etc/hdparm.conf .[/COLOR] [$1 = post] in the above script means it works on resume from sleep and hibernate under systemd, and the latter case appears to cover shutdown too.

---

