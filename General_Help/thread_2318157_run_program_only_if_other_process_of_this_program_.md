---
title: "run program only if other process of this program doesn't exist"
date: 2016-03-23
forum: General Help
---

### Post by marchello_lippi2 on 2016-03-23
Hi all, 

How do I run program only if other process of this program doesn't exist? 

Speaking of fetchmail, I receive mail from different mailboxes using crontab, some of them are each 5 minutes and other are once an hour. 
Sometimes they meet in time and I receive error: 

```
[COLOR=#000000]fetchmail: another foreground fetchmail is running at xxxxx.[/COLOR]
```

How do I prevent this error and check for other fetchmail processes before running it again? 
Thanks ahead.

$ fetchmail -V
This is fetchmail release 6.3.26+GSS+NTLM+SDPS+SSL+NLS+KRB5.

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty

---

### Post by ajgreeny on 2016-03-23
Try a pgrep command based on this which I use in my startup commands list to avoid more than one instance of skype running concurrently.
```
bash -c "sleep 20; if pgrep skype; then exit; else skype; fi"
``` You will need to edit for fetchmail, of course, and in your situation you may not need the **bash -c** suffix to the command, (nor the **sleep 20**), and if that's the case will not need the quotation marks around the command either.

---

### Post by SeijiSensei on 2016-03-23
In scripts that are invoked by cron, I write a lock file to /tmp.
```

#!/bin/bash

ADMIN=me@example.com
LOCK=/tmp/script.lock

[ -f $LOCK ] && ( echo "Script lock file found.  Exiting" | mail -s 'Lockfile found!' $ADMIN ; exit 1 )

touch $LOCK

[do stuff]

rm -f $LOCK

exit 0

```

---

### Post by marchello_lippi2 on 2016-03-24
[**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=27747"), [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"), 

thanks.

---

