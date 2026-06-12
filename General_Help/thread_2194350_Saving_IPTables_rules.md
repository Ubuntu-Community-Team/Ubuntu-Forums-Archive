---
title: "Saving IPTables rules"
date: 2013-12-17
forum: General Help
---

### Post by alfirdaous on 2013-12-17
Hello everybody,

Is there any bash script to save IPTables rules before rebooting a server??

Thanks in advance

---

### Post by Lars Noodén on 2013-12-18
Usually you could use [iptables-save](http://manpages.ubuntu.com/manpages/saucy/en/man8/iptables-save.8.html) to  save them and then [iptables-restore](http://manpages.ubuntu.com/manpages/saucy/en/man8/iptables-restore.8.html) to load them back in.  

There are some tricks that you can do to load them automatically when starting up:
[https://help.ubuntu.com/community/IptablesHowTo#Configuration_on_startup](https://help.ubuntu.com/community/IptablesHowTo#Configuration_on_startup)

---

### Post by alfirdaous on 2013-12-19
perfect, I did not get this part of code:

```

if [ -f /etc/iptables.downrules ]; then

```

from:

```

#!/bin/sh
iptables-save -c > /etc/iptables.rules
if [ -f /etc/iptables.downrules ]; then
   iptables-restore < /etc/iptables.downrules
fi
exit 0

```

---

### Post by Lars Noodén on 2013-12-20
The **-f** is a [test](http://manpages.ubuntu.com/manpages/saucy/en/man1/test.1posix.html) to see if the file exists and is a regular file, not a directory, device, symbolic link or FIFO pipe or other.

---

### Post by alfirdaous on 2013-12-20
Oh thanks [**[COLOR=#DD4814][B]Lars Noodén**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=168643"), if it exists, we restore it :)

---

