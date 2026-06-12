---
title: "Encryting tarballs via cron"
date: 2018-01-31
forum: General Help
---

### Post by cds60601 on 2018-01-31
[COLOR=#333333][FONT=&quot]Hey all[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]I have a cron job (that runs under root user) that calls a script that creates a tarball of directories /root /opt /etc and /home[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]My question is this; what would be the most efficient way to have this create the tarball and encrypt it, [/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]preferably with gpg that uses the key created for a user other than root (chris in this case).[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]I can do this if I run it as myself (of course, since I have the cipher) but Is it possible based on the scenario provided?[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I have read that openssl can be used but that is not my objective. [/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Currently (as a work-a-round), I am using 7z with a password being passed from the script (I know, not a good way of doing this but it works for now).[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Any ideas/help/alternatives would be greatly appreciated.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]TIA and cheers[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Chris[/FONT][/COLOR]

---

### Post by TheFu on 2018-01-31
If this is for backups, use a real backup tool that does encryption already - **duplicity**.

Or just create an encrypted partition with dm-crypt (cryptsetup is the tool), mount it as needed, copy the tgz files into it, then umount that area for safe keeping.

You can use gpg to encrypt anything.  I've manually done this with email when the thunderbird addon failed to work, but it is a pain.  I'd have to read the manpage to figure it out. Same for openssl.

But really, I'd just use duplicity or my preferred backup tool, rdiff-backup, and write to encrypted storage.

---

### Post by untrustytahr on 2018-01-31
TheFu is right.  It's hard to beat duplicity if you're doing backups that require things like versioning and encryption.

For future reference, if you are just tar-ing up directories from time to time and do not need versioning, you could use **gpg-zip**.  It is a script that is specifically written to create gpg encrypted tarballs.  man gpg-zip will tell you about it.

---

### Post by cds60601 on 2018-02-01
> **untrustytahr said:**
> TheFu is right.  It's hard to beat duplicity if you're doing backups that require things like versioning and encryption.

For future reference, if you are just tar-ing up directories from time to time and do not need versioning, you could use **gpg-zip**.  It is a script that is specifically written to create gpg encrypted tarballs.  man gpg-zip will tell you about it.

I did come up with a kludged way of getting what I want done. It's a mess but it works. So here's the skinny of it.

[COLOR=#333333][FONT=&amp]The cron job is created under user root so therefore I assume it is being ran as root. The root user does not have a pub/priv key created (I suppose I could go through the work flow of doing that, importing the pub keys of both root and chris, etc) then I assume it wouldn't matter (again, I stress that I am by now means fluent in gpg). [/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Syntax I came up with;[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]tar $xclude -czvpf - $backup_files | gpg --symmetric --cipher-algo aes256 --batch --passphrase=$ziggy -o $dest/$destdir/$archive_file[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]and this produces a file named: philby_2018-02-01_010001.tgz.gpg (system name, date, time, tgz.gpg)[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]The parms $ziggy is defined within the script being called with a nonsensical password that the user (chris) can use to access the gpg file. 
These tarballs are specific directories that end up on a mounted laptop drive (laptop drive in an external enclosure via USB)
Again, messy as hell but does what I need it to, lol

[/FONT][/COLOR]

---

