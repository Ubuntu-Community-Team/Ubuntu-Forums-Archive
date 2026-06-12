---
title: "How to avoid &quot;Negotiating network parameters&quot; problem when connecting to freenx"
date: 2008-06-17
forum: General Help
---

### Post by snowboard975 on 2008-06-17
I use freenx 0.7.1, and NX Client for Windows 3.2.0-10 in windows xp.

I had no problem in freenx except when suspending an nx connection and resuming it again.

NX Client always complained about "Negotiating network parameters" message and showed up an nx window for a minute and automatically disconnected with the "Connection timeout" message.

I found a solution that is suggested by torrr com and posted here. [http://readlist.com/lists/kde.org/freenx-knx/0/1991.html]("http://readlist.com/lists/kde.org/freenx-knx/0/1991.html")


To fix it, edit /usr/bin/nxserver by following command.

```
sudo gedit /usr/bin/nxserver
```

And add the following code at the beginning of the opened text file.

```
pstree -p nx| perl -e '@lines=<STDIN>; foreach $line (@lines){if ($line=~/^sshd\((\d+)\)$/) { kill 9, $1;}}'
```

Then try running NX Client to connect to nx server and you'll not see the "Negotiating network parameters" problems again!

---

