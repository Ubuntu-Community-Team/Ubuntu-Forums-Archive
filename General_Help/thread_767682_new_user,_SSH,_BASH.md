---
title: "new user, SSH, BASH"
date: 2008-04-25
forum: General Help
---

### Post by mkzimms on 2008-04-25
loaded up a new hardy server.  i went to add a new user using

```

sudo useradd -d /home/username -m username
sudo passwd username

```

that went well, but when i try to SSH under that new name the command line just gives me 

```

Last login: Fri Apr 25 21:22:11 2008 from 192.168.1.111
$

```

instead of the usual

```

Last login: Fri Apr 25 21:22:11 2008 from 192.168.1.111
username@computername:~$

```

to actually get bash i need to type "bash".  it works as normal on my original system created account, is there something im doing wrong when setting up the new user?

---

### Post by natrixgli on 2008-04-25
Hi,

try:

```
sudo usermod -s /bin/bash username
```


for more info, type 'man usermod' or 'man useradd'


Cheers,

-n8

---

### Post by Novus on 2008-04-25
why not -s /bin/bash when adding the user?

---

### Post by jose_ramirez on 2008-04-25
> **mkzimms said:**
> loaded up a new hardy server.  i went to add a new user using

```

sudo useradd -d /home/username -m username
sudo passwd username

```

that went well, but when i try to SSH under that new name the command line just gives me 

```

Last login: Fri Apr 25 21:22:11 2008 from 192.168.1.111
$

```

instead of the usual

```

Last login: Fri Apr 25 21:22:11 2008 from 192.168.1.111
username@computername:~$

```

to actually get bash i need to type "bash".  it works as normal on my original system created account, is there something im doing wrong when setting up the new user?

Hi,

Looks like you forgot to specify the user's shell, usually is /bin/bash.

Regards,

Jose

---

