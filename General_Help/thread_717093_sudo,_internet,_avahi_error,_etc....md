---
title: "sudo, internet, avahi error, etc..."
date: 2008-03-06
forum: General Help
---

### Post by kevin d on 2008-03-06
So I've got quite the perplexing problem.. I recently tried to add a user called guest which I didn't think would cause any problems.  Then I decided that having the same password for root as my user account was unsafe, so I changed the root password using sudo passwd root.  Somewhere between those two actions I got into trouble.

First of all, my gdm wasn't working but I think I managed to fix that.

Secondly, sudo doesn't do anything anymore.  I type sudo [whatever] and it prompts me for my password but then just quits silently.  I've looked in my /etc/group file and it says:

root: x:0:
nogroup: x:65534:
gdm: x:100:

Thirdly, when I start up Ubuntu (Gutsy) in recovery mode, I get these errors:

chown: 'root:utmp': invalid group
chown: 'root:tty': invalid group
chgrp: invalid group 'adm'

Fourthly, when I start up Ubuntu regularly, with the graphical display and all that, I get an alert that says "Failed to initialize HAL!".  If I hit control-alt-backspace, it gives me some avahi-daemon error. (Sorry that's not more specific, it goes by too quick to read).

If anyone has any ideas on how to fix this, or even to point me in the right direction, please send them my way.  I'd greatly appreciate it.

Also, if anyone knows how or if these are all related that would also be appreciated.

Thanks.

---

### Post by pointone on 2008-03-06
If your group file only contains those three lines, then you're missing A LOT of groups. Specifically, you're missing the admin group, which would explain sudo not working, and you're missing utmp, tty, and adm, which would explain the missing group errors. My /etc/group contains 60 groups, for example. Your last problem is most likely releated.

Check to see if you have a file "/etc/group-" or "/etc/group~"; these would be backups and could be used to restore your groups.

---

### Post by kevin d on 2008-03-06
Hey, thanks so much.  I copied /etc/groups~ to /etc/groups and everything works fine now.  Thanks again for your help!

---

