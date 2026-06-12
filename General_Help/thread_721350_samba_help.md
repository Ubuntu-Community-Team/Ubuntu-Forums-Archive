---
title: "samba help"
date: 2008-03-11
forum: General Help
---

### Post by fouadk on 2008-03-11
hi everyone...

i have successfully joined my ubuntu machine to a windows 2003 sever domain....
i have also shared some files and those files were made available to windows machine....

my question is that when a user tries to see the shares of my ubuntu it needs to provide a password....on the windows server , the administrator have access to everything....if the username administrator and the administrator password are provided....my ubuntu machine is not letting them in....only the username and password of the local ubuntu user are allowed....

how to enable to windows server administrator password to be used in order to let him in...

thanks in advance...

---

### Post by _samba_ on 2008-03-11
Did you add administrator account to local and samba users? This should be the same username and password that you log onto to the Windows PC with.

---

### Post by bharadwaj on 2008-03-11
At first this was the issue which kindda made me think...but then this was fixed after i added another stand alone user for samba ......

---

### Post by fouadk on 2008-03-11
what i did is followed some tutorial on the net and changed the smb.conf and kerberos configuration file and then i did:
```
net ads join -U administrator
```

what next ???

how to create a samba user ???

please help

thanks in advance

---

