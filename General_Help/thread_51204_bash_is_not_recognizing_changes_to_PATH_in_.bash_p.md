---
title: "bash is not recognizing changes to PATH in .bash_profile"
date: 2005-07-22
forum: General Help
---

### Post by Third Thoughts on 2005-07-22
Hey all, I'm having a kind of weird issue that I can't seem to find any literature on. I'm trying to set it up so that my bash enviroment recognizes that I have a ~/bin folder, and puts this folder in my PATH. I can't send the text that was originally in the relavent part of my bash profile, because I edited it to remove the if statement that was there. Now it just reads ```
 PATH="$PATH:~/bin" 
```. What is probably worth noting is that my ~/bin folder is a symbolic link to a folder on another partition. I'm running a dual boot with FC4 so I have three partitions, one for Ubuntu files, one for FC4 files, and one for my general purpose files. Is this sym link some how an issue for bash? Any help folks can offer with this would be useful because I'm sick of typing ~/bin when I want to run one of my own scripts.

~Andrew S.

---

### Post by kinnla on 2005-07-23
i have a similar problem. i also want a directory (/usr/java/j2sdk1.4.2_08/bin) included in my path. i choosed to add it to the appropriate line at /etc/profile where $PATH is set, in order to have an effect for all accounts. i performed a restart, but no result. echo $PATH shows the same path as before my edit.

how can that be? is there a kind of caching of bootup data, preventing ubuntu from reading the actual files?

---

### Post by kinnla on 2005-07-24
i didn't look carefully. echo $PATH doesn't show my old path, it shows a different one from the one set at /etc/profile:>  echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
quote from /etc/profile (original version, before adding the java dir):> if [ "`id -u`" -eq 0 ]; then
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
else 
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
fi  
compare the order of directories.

so it seems to me that /etc/profile is not evaluated at all. but where else the path is set? does anybody which file it is?

---

### Post by kinnla on 2005-07-24
got it: /etc/login.defs

cmp: [http://www.ubuntuforums.org/showthread.php?t=51348](http://www.ubuntuforums.org/showthread.php?t=51348)

so there are differences between distributions.

---

### Post by kinnla on 2005-07-24
no, it is not working. still the old path.

---

### Post by kinnla on 2005-07-24
i set up the path at /etc/security/pam_env.conf now, and it works.

---

### Post by Third Thoughts on 2005-07-28
Thanks for tip, it worked for me. 

~Andrew S.

---

