---
title: "Seahorse/GnuPGP problem"
date: 2006-10-31
forum: General Help
---

### Post by DW5 on 2006-10-31
I upgraded to Edgy last week.  Thunderbird enigmail worked fine.  Sometime around midday yesterday, I rec'd the following error when trying to send mail:

```
gpg command line output:

/usr/bin/gpg --charset utf8 --batch --no-tty --no-auto-check-trustdb --status-fd 2 --comment 'Using GnuPG with Mozilla - http://enigmail.mozdev.org' --digest-algo sha1 -t --clearsign -u 0x2A925EC1 --passphrase-fd 0 --no-use-agent

gpg:/home/dwilliams/.gnupg/gpg.conf:198: invalid option
gpg:/home/dwilliams/.gnupg/gpg.conf:211: invalid option
```

I looked at the gpg.conf file, those lines read:

Line 198 reads: 
```
 '·`'·
```
Line 211 reads:

```
  '·x'·ent-info /home/dwilliams/.gnome2/seahorse-Eh0YiU/S.gpg-agent:8960:1 
```

These characters are bizzare and don't render here when pasted in the same as they render in gedit, so I'm guessing they are coded somehow(?).

Using system monitor, I checked to see if a seahorse agent is running.  I see seahorse-daemon there.

I started seahorse to check keys, but all the keys including mine are gone!

I have them backed up, so I selected import keys in Seahorse. It allows me to browse the backup key files.  I selected the key, but seahorse doesn't import them. (This is the newest seahorse in repos). I did this several times, and rebooted several times in between.

When I try to reimport my keys from the command line (using gpg --import), I get invalid option errors in lines 198, 211, and 212.

I've googled and searched the forums, but don't see anything similar to this.

Any ideas about what is wrong?  Should I uninstall seahorse and reinstall it? or do I need to reinstall gpg, or ...?

Thanks for any help.

DW

---

### Post by ryan on 2006-11-16
> **DW5 said:**
> I upgraded to Edgy last week.  Thunderbird enigmail worked fine.  Sometime around midday yesterday, I rec'd the following error when trying to send mail:

```
gpg command line output:

/usr/bin/gpg --charset utf8 --batch --no-tty --no-auto-check-trustdb --status-fd 2 --comment 'Using GnuPG with Mozilla - http://enigmail.mozdev.org' --digest-algo sha1 -t --clearsign -u 0x2A925EC1 --passphrase-fd 0 --no-use-agent

gpg:/home/dwilliams/.gnupg/gpg.conf:198: invalid option
gpg:/home/dwilliams/.gnupg/gpg.conf:211: invalid option
```

I looked at the gpg.conf file, those lines read:

Line 198 reads: 
```
 '·`'·
```
Line 211 reads:

```
  '·x'·ent-info /home/dwilliams/.gnome2/seahorse-Eh0YiU/S.gpg-agent:8960:1 
```

These characters are bizzare and don't render here when pasted in the same as they render in gedit, so I'm guessing they are coded somehow(?).

Using system monitor, I checked to see if a seahorse agent is running.  I see seahorse-daemon there.

I started seahorse to check keys, but all the keys including mine are gone!

I have them backed up, so I selected import keys in Seahorse. It allows me to browse the backup key files.  I selected the key, but seahorse doesn't import them. (This is the newest seahorse in repos). I did this several times, and rebooted several times in between.

When I try to reimport my keys from the command line (using gpg --import), I get invalid option errors in lines 198, 211, and 212.

I've googled and searched the forums, but don't see anything similar to this.

Any ideas about what is wrong?  Should I uninstall seahorse and reinstall it? or do I need to reinstall gpg, or ...?

Thanks for any help.

DW

I had something similar happen.. open gpg.conf and edit out the garbage on those 2 lines and things should work. Also uncheck the "use agent" option in your enigmail options. Seahorse daemon  I think took the place of "seahorse agent". Delete seahorse agent from your sessions and add "seahorse daemon". Hope this helps.

---

