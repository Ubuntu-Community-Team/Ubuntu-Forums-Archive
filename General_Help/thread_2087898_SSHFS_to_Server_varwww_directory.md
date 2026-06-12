---
title: "SSHFS to Server var/www directory"
date: 2012-11-24
forum: General Help
---

### Post by WASHAD on 2012-11-24
Be gentle please, new to the server stuff please. 

I've set up an Ubuntu Server on a virtual box. I want to edit the index.php file from my host machine, so I can edit it from a graphical environment. I read that SSHFS is the way to do that. I can get the SSHFS command to work - pointing to the users directory, but I can't get the syntax to have it point to the var/www directory. 

Can someone point me in the right direction - including setting the permissions accordingly. 

SSHFS stevej@192.168.1.68: ~/RemServer "/var/www"

...But I can't get the syntax correct for the var/www. 

Thank you, 

SteveJ

---

### Post by beboylips on 2012-11-25
I don't know how to do it your way, but may I suggest using nano over ssh.

```

ssh username@host
nano /var/www/index.php

```

Nano is pretty amazing and can even beat graphical text editors.

-Beboy

---

### Post by M!K3_$ on 2012-11-25
From the man page:

[INDENT]sshfs [user@]host:[dir] mountpoint [options][/INDENT]


This means that you will want to do something like:

```
ssfs stevej@192.168.1.68:/var/www/ ~/sshfs-directory
```


(This will require a directory in your home called "sshfs-directory")

---

### Post by WASHAD on 2012-11-26
> **beboylips said:**
> I don't know how to do it your way, but may I suggest using nano over ssh.

```

ssh username@host
nano /var/www/index.php

```

Nano is pretty amazing and can even beat graphical text editors.

-Beboy

Thank you for the suggestion, I will give it a go -- still like to find my problem nonetheless. 

Cheers.

---

### Post by WASHAD on 2012-11-26
> **M!K3_$ said:**
> 
```
ssfs stevej@192.168.1.68:/var/www/ ~/sshfs-directory
```

(This will require a directory in your home called "sshfs-directory")

...So I just had the folder order backwards --- what an idiot!

Thank you for the help, that works. 

For anyone reading this later, this allows me to treat the remote server path "var/www" as a locally mounted file - so that I can remotely edit my web pages graphically - Awesome. 

Cheers.

---

### Post by M!K3_$ on 2012-11-27
Great to hear you got it working! Always remember to use the man page when in doubt:
```
man sshfs
```

And you should mark the thread as 'solved' to help people searching in the future. :)

---

### Post by WASHAD on 2012-11-29
..oh, that feature is back. I recall the marked as solved going away some time ago. 

Marked it is....have a great day and thank you again for your help. 

Cheers.

---

