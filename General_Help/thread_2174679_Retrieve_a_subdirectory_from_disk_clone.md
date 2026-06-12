---
title: "Retrieve a subdirectory from disk clone"
date: 2013-09-15
forum: General Help
---

### Post by emagar on 2013-09-15
Dear forum members,

I messed up ownership/permissions of the whole /var/lib directory while attempting to configure mysql. The problem is similar to this [http://askubuntu.com/questions/48629/problems-with-sudo-permissions-var-lib-sudo-owned-by-uid](http://askubuntu.com/questions/48629/problems-with-sudo-permissions-var-lib-sudo-owned-by-uid). 

I cloned my whole ubuntu partition with clonezilla some time ago in a portable drive. There should be a way of recovering the permissions for most files in /var/lib from the cloned version. Any clues about how I could proceed?

Thank you in advance, 

--yomero

---

### Post by steeldriver on 2013-09-15
You could use something like

```
find /path/to/old/var/lib -printf "%m %P\n" > permissions.txt
```

which will print the octal permissions (%m) and pathname relative to /path/to/old/var/lib (%P) to a file called permissions.txt - you may want to replace the \n (newline) termination by a null byte \0 depending whether you want it to be human readable or processed by a script e.g. if you want to script the subsequent chmods, then something like this maybe

```
find /path/to/old/var/lib -printf "%m %P\0" > permissions.txt
```

```
while read -rd $'\0' perm file; do [[ -e "/var/lib/$file" ]] && echo chmod "$perm" "/var/lib/$file"; done < permissions.txt
```

Good luck

---

### Post by jamesisin on 2013-09-15
You could make a cloned drive from your CloneZilla files.  Then you would have access to that new clone from your current system.  Then I suppose you could use something like rsync to fix the permissions, but that could be dangerous depending on how much might have changed since you made that clone.  I don't know if rsync has a permissions-only hook, but maybe there is such a tool out there.

---

### Post by emagar on 2013-09-16
Thank you steeldriver. I will attempt what you propose in the evening, when my toddler gives me some peace. I will report on my status then.

---

