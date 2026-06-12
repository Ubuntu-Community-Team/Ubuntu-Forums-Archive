---
title: "chmod/chown write permission issues"
date: 2014-11-06
forum: General Help
---

### Post by AuroraDizon on 2014-11-06
Hi I have a Joomla site but I have been having some issues with getting the write permissions correct.  

Recently I have tried to: 
```
find . -type d -print0 | xargs -0 chmod 0755 # for directories
find . -type f -print0 | xargs -0 chmod 0644 # for files
```

Yet whenever I ```
find . -type d -print0 | xargs -0 chmod 0755 # for directories
``` or ```
sudo find . -type d -print0 | xargs -0 chmod 0755 # for directories
``` I still end up with a chmod: changing permissions of './templates/example'.  Operation not permitted.

---

### Post by steeldriver on 2014-11-07
"Operation not permitted" usually indicates some kind of extended file attributes (beyond the usual *nix permission bits) - what do

```

ls -l ./templates/example

lsattr ./templates/example

```

say?

---

### Post by AuroraDizon on 2014-11-07
-rw-r--r-- 1 www-data www-data 1185 Oct  1 06:52 editor.css
-rw-r--r-- 1 www-data www-data 1443 Oct  1 06:52 error.css
-rw-r--r-- 1 www-data www-data  328 Oct  1 06:52 error_rtl.css
-rw-r--r-- 1 www-data www-data 2730 Oct  1 06:52 general.css
-rw-r--r-- 1 www-data www-data   31 Oct  1 06:52 index.html
-rw-r--r-- 1 www-data www-data 1933 Oct  1 06:52 offline.css
-rw-r--r-- 1 www-data www-data  548 Oct  1 06:52 offline_rtl.css
-rw-r--r-- 1 www-data www-data  896 Oct  1 06:52 system.css
-rw-r--r-- 1 www-data www-data  608 Oct  1 06:52 toolbar.css



-------------e-- ./templates/index.html
-------------e-- ./templates/protostar
-------------e-- ./templates/beez3
-------------e-- ./templates/system

2 different folders but I didn't think that would make a difference as there are many directories that have the Operation not permitted error.

---

### Post by sisco311 on 2014-11-07
Only the owner of a file or root is allowed to change its permissions. If you want to change the permissions as root, you have to put `sudo' in front of the chmod command. In your example you run the find command as root. ;)

Please check out: [https://help.ubuntu.com/community/RootSudo#Downsides_of_using_sudo](https://help.ubuntu.com/community/RootSudo#Downsides_of_using_sudo)

---

### Post by AuroraDizon on 2014-11-07
I did sudo. Do I have to su into root first? Because it still gave me the error.

I'm also having problems uploading images via Joomla, is that probably the write permissions too?

---

### Post by matt_symes on 2014-11-07
Hi

Read Sisco's post again as he is bang on the money with his reply.

You have elevated the permissions for the find command and not for the chmod command. 

You need sudo in front of the chmod command as well.

Remember that the pipe will create a new subshell without the elevated privileges.

Kind regards

---

### Post by steeldriver on 2014-11-07
I still suspect that "Operation not permitted" indicates more than a simple *nix permission issue (which would usually give a "Permission denied" error) - for example the parent directory could be immutable or append-only? I seem to remember also seeing "Operation not permitted" when the target filesystem is ro

---

### Post by AuroraDizon on 2014-11-07
Not sure what was wrong with the one I tried to use but this one seems to work: 
```
find -type f -exec chmod 644 {} \;
find -type d -exec chmod 755 {} \;
```

---

### Post by matt_symes on 2014-11-07
Hi

> **AuroraDizon said:**
> Not sure what was wrong with the one I tried to use but this one seems to work: 
```
find -type f -exec chmod 644 {} \;
find -type d -exec chmod 755 {} \;
```

Your previous commands work for me. Here's an example for one of them.

```

matthew-laptop:/home/matthew/test:4 % ls -l
total 4
-rwxr-xr-x 1 matthew matthew 113 Nov  6 18:25 s.sh*
matthew-laptop:/home/matthew/test:4 % find . -type f -print0 | xargs -0 chmod 0644
matthew-laptop:/home/matthew/test:4 % ls -l
total 4
-rw-r--r-- 1 matthew matthew 113 Nov  6 18:25 s.sh
matthew-laptop:/home/matthew/test:4 %
```

Interesting point about the error message steeldriver. 

Kind regards

---

