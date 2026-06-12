---
title: "Ubuntu 14.04 backup (deja-dup) password resetting"
date: 2016-02-03
forum: General Help
---

### Post by ben198 on 2016-02-03
I was testing  the Ubuntu back up application (deja-dup) and gave it a  password too.
Now I would like to start from the beginning without a password. The program settings do
not allow any change any more.
Should I uninstall the application  or how can I get password settings back?

---

### Post by deadflowr on 2016-02-03
Open a terminal and run
```
dconf -reset -f /org/gnome/deja-dup/
```
then open the program called Password and Keys and highlight the Listing for Backup encryption Password, right click it and select delete.
If no backup encryption password is listed, then all is well.
I think that option exists only if you selected* remember password*.
When you create a new backup simply do not use any password, and don't select *remember password*.

Hope it works, or helps.

---

### Post by ben198 on 2016-02-06
Getting the following result with sudo and without sudo:

~$ sudo dconf -reset -f /org/gnome/deja-dup/

error: unknown command -reset

Unknown command '-reset'

---

### Post by deadflowr on 2016-02-06
Sorry, remove the - from reset.
```
dconf reset -f /org/gnome/deja-dup/
```
And do not sudo it.

---

### Post by ben198 on 2016-02-06
Hmm.. Still something wrong?

No reaction at all to that command.

And for that matter Ubuntu version is 14.04 if that makes any difference. ;)

---

### Post by deadflowr on 2016-02-06
What reaction do you expect?
The command itself, will return nothing when run properly.

Is the settings in the backups different from what you had set?

---

### Post by ben198 on 2016-02-06
I do not remember how I set the backup settings originally. I only vaguely remember I set a password but In any case I am able to open the deja-dup file in my "home folder" without a password.
It contains several "duplicity-full.20160116T191245Z.vol1.difftar.gz" -files and some few "duplicity-full.20160116T191245Z.manifest" -files.

When I open Password and Keys program I cannot find any  "Listing for Backup encryption Password", so I suppose the backups are not encrypted at all?
There is only  some PGP keys which are for my e-mail.

Can I continue backuping normally or should I delete the original deja-dup file altogether and start from the beginning?

The only thing I hope, I do not mess up everything at this stage. The present backups are not yet important.

---

### Post by deadflowr on 2016-02-06
So...
When you open Backups, if you try a restore does it show the old location you setup to backup to, or is it showing some other place?

When you click on restore, it'll open a first page showing where the backups should be found, and gives you the ability to change it.
When you set the location and then if click on Forward, it will scan that location for the manifest file, and then open a second page 
with a date listing  dropdown menu you can toggle to select a certain date when the backup was made.
If no other dates are listed in the dropdown then no other backups exist.
If no date exists, then no backup exists.
If no backup exists, I'd say delete those old ones, if you want.

Also: basically since there does not seem to be any gpg extensions in those files, then it's unencrypted, fyi.

Does any of that make any sense?

---

### Post by ben198 on 2016-02-07
It shows the old and original  deja-dup file as location. Also shown as the storage location.

There are  9 dates to restore from.  Let 's  speculate, if I accidentally restore an old date, it could cause
some problems for instance in Keepass data.

Can I delete all except the latest one?

Or, is it causing any harm if I delete all of them?

I still cannot see the starting page where the password
and encrypting alternatives were shown.

I understand that as long as I backup my home folder only, I cannot damage Ubuntu itself?

---

