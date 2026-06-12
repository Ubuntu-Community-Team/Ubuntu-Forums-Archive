---
title: "Prob with the Administrative apps not working."
date: 2006-10-23
forum: General Help
---

### Post by jms1989 on 2006-10-23
Yesterday, I was fiddling with the /etc/hosts file and apparently, I didn't realize this, the file is used by other things allong with Apache. I guess when I deleted the host name to add a made up domain to setup a website on my pc along with subs. I didn't know the administrative apps use the files.

Is there some possiblity I could split the file, one for the system and another for only Apache? That would help pervent me from having to restore the system for the third time for the same purpose. Btw, it did it to me this afternoon before this post.

---

### Post by bettlebrox on 2006-10-23
I'm not quite sure what your trying to do. But, if you could set the localhost address to some made up address like so:


127.0.0.1 localhost.localdomain localhost machinename mysuperhostname.com madeupname.com

Just make sure NOT to remove the references to localhost* and your system-name.

---

