---
title: "Since Utopic, Deja-Dup prompts to unlock keyring"
date: 2014-12-07
forum: General Help
---

### Post by HerixFromParis on 2014-12-07
A few weeks ago, I ugpraded to 14.10 "Utopic Unicorn". Flawless, except ...
I have a daily back-up with a password stored somewhere.
If I understand correctly, the backup tool is Duplicity with Deja-dup as front-end and the password is stored in the Gnome keyring with Seahorse as front-end.

I typed the password once, then never again, that is, until upgrade. Something along the line of "keyring unlocked at log-in". Now, a few minutes after logging in, a prompt asks for the password to unlock the keyring.

How can I revert to the previous behaviour ? I looked around on the Net, it seems I am not the only one with this issue, but so far I wasn't able to find a clear answer. Help ?

Thxx

---

### Post by CantankRus on 2014-12-07
Have you changed your user account to automatic login or do
you still type it at the greeter? 
You need to manually logon to unlock your login keyring where your Backup encryption password is stored. 

You could try saving your passphrase again.
Delete the Backup encryption password (check and copy password before deleting) from your Login keyring and then
open backups and choose to run a backup now. 
It will ask to enter the encryption password. (use the same password as before)
**Make sure to tick the "Remember me" box.**

---

### Post by HerixFromParis on 2014-12-13
OK, that was this : automatic login. (via /etc/lightdm/lightdm.conf)
Disabling it should do the trick. We'll see tomorrow. Then I'll have to remember how to enable automatic login again ...
Thanks :-)

---

