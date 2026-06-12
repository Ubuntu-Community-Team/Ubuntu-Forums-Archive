---
title: "NFS with a different user"
date: 2007-09-16
forum: General Help
---

### Post by jmvidalvia on 2007-09-16
Can I connect to a server with NFS using a username which only exists in the server, not in my local machine? just like you can do with Samba...
Thanks a lot!

---

### Post by JinxAu on 2007-09-16
Gday jmvidalvia,

Although I haven't done it myself, it should be possible using the "map_static" option. Described as:
> map_static

    This option allows you to specify the name of a file that contains a static map of uids and gids. For example, map_static=/etc/nfs/vlight.map would specify the /etc/nfs/vlight.map file as a uid/gid map. The syntax of the map file is described in the exports(5) manual page.

the /etc/nfs/vlight.map file would look something like:
> # Mapping for client homer:  
# remote local  
uid     0-99      -    # squash these  
uid  100-500   1000    # map 100-500 to 1000-1500  
gid     0-49      -    # squash these  
gid   50-100    700    # map 50-100 to 700-750  

Cya round
Jinx

---

### Post by jmvidalvia on 2007-09-17
Thank you very much, although I read it is not usefull for several users...
:(
In my office 25 are using XP, so they connect to the server with Samba: I guess that in that case, even for the 5 who use Linux would be better to use samba. ¿how can I match id and gid for so many people using NFS?
Thank you very much...

---

### Post by JinxAu on 2007-09-17
Gday jmvidalvia,

It might be worth looking into using LDAP to manage your users. It's a bit complex to get your head around to start with, but it will mean you can make one set of user and group credentials available to each machine on the network.

Check out [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer) for more info on LDAP.

Cya round
Jinx

---

### Post by jmvidalvia on 2007-09-18
Thank you very much: I will try to do my best to leard about LDAP.
Best regards,

---

