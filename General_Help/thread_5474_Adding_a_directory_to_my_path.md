---
title: "Adding a directory to my path"
date: 2004-11-18
forum: General Help
---

### Post by Dustismo on 2004-11-18
Hi,

I just installed the java SDK and I want to add the java bin directory to my global path.  Nothing I try seems to work, aargh..  I edited /etc/profile to look like this, but it doesn't work.  

```
 
PATH="/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/usr/bin/X11:/usr/games:/usr/local/j2sdk1.4.2_06/bin:"

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

export PATH

umask 022


``` 

Can somebody help??

thanks,
Dustin

---

### Post by blackknight on 2004-11-18
you need to edit /etc/bash.bashrc instead of /etc/profile.
good luck
(^_^)

---

### Post by jdong on 2004-11-18
**/etc/environment** should be used. Example:
 
  ```
PATH=$PATH:/usr/something/somethingelse
```

---

