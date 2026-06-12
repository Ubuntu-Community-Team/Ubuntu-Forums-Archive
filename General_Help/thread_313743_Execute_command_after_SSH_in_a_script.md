---
title: "Execute command after SSH in a script?"
date: 2006-12-06
forum: General Help
---

### Post by bigblop on 2006-12-06
I have a script:

```

#!/bin/sh
xterm -e 'ssh <host> -l <user>'
xlassie -bell -clickcommand mozilla-thunderbird -pop <server> -username <user> -password <pass>

```

but only the SSH command are completed. After I have entered the password xlassie never gets started. Any hints?

---

### Post by djf_jeff on 2006-12-06
You must put the command right after the ssh command, much like

```

#!/bin/sh
xterm -e 'ssh <user>@<host> \'xlassie -bell -clickcommand mozilla-thunderbird -pop <server> -username <user> -password <pass>\''

```

---

### Post by bigblop on 2006-12-06
That does not work. I have tried:

```

xterm -e 'ssh myuser@myhost \'xlassie -bell -clickcommand mozilla-thunderbird -pop mailserver -username mailuser -password mailpass\''

```

---

### Post by hegenious on 2006-12-06
I advise you to first test it in a terminal before putting it in a script
the syntax is: **ssh -l user host command**
no quotes, nothing.
what does that give you?

and if xlassie is a graphical X application, you must forward X11 in order to see it displayed.
then it would be ssh -X -l user host xlassie -bell -clickcommand mozilla-thunderbird -pop <server> -username <user> -password <pass>

---

