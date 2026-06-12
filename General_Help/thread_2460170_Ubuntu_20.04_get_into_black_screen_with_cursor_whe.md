---
title: "Ubuntu 20.04 get into black screen with cursor when ubuntu logo is displaying"
date: 2021-04-03
forum: General Help
---

### Post by owenizedd on 2021-04-03
Hi,

Last night I did *sudo do-release-upgrade *from Ubuntu 18.04 to 20.04 with several errors it shows something like *too many errors, stopping* then it shows list of applications that have issue.

Now I can't boot, now I see a lot of error when I do things like: *sudo apt update *or *sudo apt install* it shows some errors, but most common is *ImportError: /usr/local/lib/x86_64-linux-gnu/libstdc++.so.6: version 'GLIBCXX_3.4.26*[I]' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.6.0)
[/I]But when I try to install it (*sudo apt install libstdc++6*) it shows:

[I]....
....
use 'sudo apt autoremove' to remove  them.
0 upgraded, 0 newly installed, 0 to remove then and 0 not upgraded.
381 not fully installed or removed.
After this operationo, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]


[/I]Like it's not completed installing when upgrading my ubuntu version last night, when I press enter, at the end of output, it was showing error something like

[I]errors were encountered while processing :

[/I]and show list of appliacation that causes issue:

[LIST]
[*]dbus 
[*]fprintd 
[*]ubuntu-system-server 
[*]... and list goes on 
[/LIST]


But when I try to do install again, now at the end of the output just showing:
*No apport report written because MaxReports is reached already*

This is my working laptop, and I can't access the desktop, all of command i access from ctrl + alt + f4 to get to terminal on black screen cursor, and yes I have sudo access.

I check at /var/crash, it has *dbus.0.crash* and *samba-common-bin.0.crash* file
How can I fix this issue? I think this is because the upgrade on *sudo do-release-upgrade *have some issue and when i restart ubuntu not working anymore.
However now when i use *cat /etc/issue *it showing 'Ubuntu 20.04.02 LTS'

Please let me know if this is possible to fix, Because tomorrow I need to use this laptop, it was my mistake not doing any backup thinking it will successfully.

---

### Post by Bashing-om on 2021-04-04
owenizedd - Hello
and Ouch !

> 
381 not fully installed or removed.


is worrisome - did you not "update" prior to the release-upgrade ?

However, let us see what we can do to fix the install.
try:
```

sudo apt autoclean
sudo apt autoremove
sudo apt clean
sudo apt update
sudo apt apt upgrade
sudo apt -f install
sudo dpkg --configure -a
sudo dpkg -C

```

See here what the package manager can do for us.

[INDENT]only a maybe
[INDENT][INDENT]Yes
[/INDENT][/INDENT][/INDENT]

---

