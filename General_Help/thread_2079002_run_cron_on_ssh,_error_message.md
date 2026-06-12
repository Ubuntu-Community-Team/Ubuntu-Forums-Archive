---
title: "run cron on ssh, error message"
date: 2012-11-01
forum: General Help
---

### Post by dolbyater on 2012-11-01
how to run the script below

```
* * * * * /usr/bin/wget -O - -q "http://example.com/scheduler/cron"
```

 
when i run the script, the error message show as below:
```
$ * * * * * /usr/bin/wget -O - -q "http://website.com/?q=admin/settings/scheduler/cron"
-sh: CHANGELOG.txt: not found
$ 30 15 * * * /usr/bin/wget -O - -q "http://website.com/?q=admin/settings/scheduler/cron"
-sh: 30: not found
```


can the script above run in ssh (using putty software)

---

### Post by Habitual on 2012-11-01
```
* * * * * /usr/bin/wget -O - -q "http://example.com/scheduler/cron"
```is not a script, but a cron entry

To use that in a script as a cron entry. add this to say, ~/cronwget.sh
```
#!/bin/bash
/usr/bin/wget -O - -q "http://example.com/scheduler/cron"

```then make it executable for you only.
```
chmod 700 ~/cronwget.sh
```and ***this*** to cron
```
* * * * * /path/to/cronwget.sh
```

---

### Post by dolbyater on 2012-11-01
> **Habitual said:**
> ```
* * * * * /usr/bin/wget -O - -q "http://example.com/scheduler/cron"
```is not a script, but a cron entry

To use that in a script as a cron entry. add this to say, ~/cronwget.sh
```
#!/bin/bash
/usr/bin/wget -O - -q "http://example.com/scheduler/cron"

```then make it executable for you only.
```
chmod 700 ~/cronwget.sh
```and ***this*** to cron
```
* * * * * /path/to/cronwget.sh
```


if i want to run cron every 5 minute, how to do it?

---

### Post by Habitual on 2012-11-01
```
*/5 * * * * /path/to/cronwget.sh
```

Stolen from [http://www.thegeekstuff.com/2011/07/cron-every-5-minutes/](http://www.thegeekstuff.com/2011/07/cron-every-5-minutes/)

---

