---
title: "Synaptic errors because of conexant"
date: 2007-02-08
forum: General Help
---

### Post by YinZen on 2007-02-08
I recently only had access to a dial up connection, and because i use the net on a regular basis i wanted to get the modem working in my preferable OS. Now ive got broadband its backfired and wont let me use synaptic, dpkg or infact pretty much any packadge management tools in ubuntu. I seem to have tryed everything that people have done during similar problems, the most promising being:
```
sudo dpkg --remove --force-depends --force-remove-reinstreq conexant
```
but this gives the output:
```
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 136299 files and directories currently installed.)
Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 conexant

```
If i try and open synaptic i get..

```
E: The package conexant needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

..and then its just a blank packadges window with no options to uninstall or remove.
Would clearing the cache help?

Thanks if you can help
'YinZen'

---

### Post by YinZen on 2007-02-09
Anyone?? Please!!

---

### Post by YinZen on 2007-02-09
Ok, after 2 days i managed to figure it out for my self.

Just in case anybody else has the same problem my solution was to delete any files that referenced conexant in /var/lib/dpkg/info in their filenames. Then i opened up a terminal and ran:
```
sudo dpkg --remove --force-depends --force-remove-reinstreq conexant
```
and it executed smoothly and now everyting is back to normal.

---

### Post by moschops on 2007-03-09
Thanks for posting your experience - I had the same problem but your fix didn't work for me.

In the end I had to dig into the dpkg directories to locate the script that was causing the error:

```
/var/lib/dpkg/info/conexant.postrm 
```

and comment out the line that reads:

```
rmmod hsfserial hsfengine hsfbasic2 hsfosspec
```

then I was able to 

```
sudo apt-get remove conexant
```

successfully.  I don't know anything about how apt-get works but it looks like the fact that the rmmod command included "ERROR" in its output caused the problem because this script should exit with status 0 regardless of what goes wrong inside of it (except for bad arguments).  Maybe rmmod was causing the script to bomb out early before the exit 0?

---

