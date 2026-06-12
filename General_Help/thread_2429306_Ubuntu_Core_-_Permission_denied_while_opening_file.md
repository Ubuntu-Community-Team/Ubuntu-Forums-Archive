---
title: "Ubuntu Core - Permission denied while opening file"
date: 2019-10-16
forum: General Help
---

### Post by izidir on 2019-10-16
Hi everybody,

I've looked around but didn't find any answer to my problem.

I'm trying to setup a nextcloud server on a raspberry running ubuntu core.

So i'm doing my config through ssh and i need to modify this damn config.php

My problem is when i want to open it with nano i get "Error Reading config.php Permission denied"

while using: user access, user with sudo and even with root access.

Can anybody explain how i should do it ?

Thanks a lot :)

---

### Post by deadflowr on 2019-10-16
Where's the file located?

In the user /home directory or in /var or /snap?

---

### Post by izidir on 2019-10-16
the file is located in /var/snap/nextcloud/16406/nextcloud/config/config.php

---

### Post by deadflowr on 2019-10-16
Then it won't be editable since that is mounted as read-only.
It's unchangeable too.
Only snap files located in the user's home folder are editable.

Edit: nevermind, I'm thinking /var/lib not /var/snap.
Something else is going on here, it should be editable in that particular folder.
try it with current instead of he ### directory (the 16406 directory,
current always points to the current snap image version directory, so current would be 16406)
So try
```
sudo nano /var/snap/nextcloud/current/nextcloud/config/config.php
```
and see if that does it.

---

### Post by #&amp;thj^% on 2019-10-16
Snaps are designed to have a limited interface for configuration. Powerful (and easily misconfigured).
I won't use nextcloud Snap see if this will work for you and more user control: [https://github.com/nextcloud/nextcloud-snap#configuration](https://github.com/nextcloud/nextcloud-snap#configuration)
Or maybe someone that like the Snap package will help here. 
Kind Regards

---

### Post by izidir on 2019-10-16
@deadflowr

No it didn't work

@1fallen

THANKS i didn't tough to look at the github page. The editing didn't work but i found a way around with the nextcloud occ command

I was looking to add trusted domains and the following commands did the trick

```
sudo nextcloud.occ config:system:get trusted_domains

sudo nextcloud.occ config;system:set trusted_domains X --value="your IP/domain.name" 
```

With X being the line you want to add/change.

---

