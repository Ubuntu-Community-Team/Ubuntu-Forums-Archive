---
title: "Using tar to create a gzip tarball"
date: 2021-12-26
forum: General Help
---

### Post by sniper8752 on 2021-12-26
I am trying to backup folders.  Here is the command that I am using:

```
[FONT=monospace][COLOR=#000000]root@mail:~# tar cvzf /etc/postfix /etc/dovecot/ /var/vmail/ /home/user0/ /home/user1/ .
[/COLOR]...
[FONT=monospace][COLOR=#000000]/etc/dovecot/dovecot.conf[/COLOR]
...
[FONT=monospace][COLOR=#000000]tar: /etc/postfix: Wrote only 8192 of 10240 bytes [/COLOR]
tar: Child returned status 2 
tar: Error is not recoverable: exiting now[/FONT][/FONT]
[/FONT]
```

---

### Post by HermanAB on 2021-12-26
I would do a dry-run just listing files. Use -v for verbose mode to list the files and use /dev/null as output to avoid the overhead of writing the tarball. Exclude -v or -z if you just want to see tar errors.

tar -cvzf /dev/null targetdir

---

### Post by schragge on 2021-12-26
What/where is the name of the tarball you want to create? As it stands now, you command tries to write to the file **/etc/postfix** and fails because there's directory with the same name.

**Update**. Now I see **HermanAB** already mentioned this in the edit reason.

---

### Post by The Cog on 2021-12-26
Yup. The first argument after the -f flag is the name of the tarball file you want to create.
"tar cvfz ..." will create an archive called z. That. used to catch me out from time to time

---

