---
title: "Dovecot doveadm scripting issue"
date: 2016-09-09
forum: General Help
---

### Post by SchnappiJedi on 2016-09-09
Have used script below with Dovecot forever to purge emails. 
[I]
#!/bin/bash
#
DOVEADM="/usr/bin/doveadm";

$DOVEADM expunge -A mailbox Drafts savedbefore 365d
$DOVEADM expunge -A mailbox Sent savedbefore 365d
$DOVEADM expunge -A mailbox Junk savedbefore 30d
$DOVEADM expunge -A mailbox Trash savedbefore 30d[/I]

On a new server, get:
sudo: /script-name.sh: command not found

yet using
[I]
sudo doveadm expunge -A mailbox Drafts savedbefore 365d
sudo doveadm expunge -A mailbox Sent savedbefore 365d
sudo doveadm expunge -A mailbox Junk savedbefore 30d
sudo doveadm expunge -A mailbox Trash savedbefore 30d[/I]

As individual command works. 

Is there something wrong with original script?

---

### Post by SchnappiJedi on 2016-09-09
Never mind. Forgot to run.

chmod +x /script.sh

---

