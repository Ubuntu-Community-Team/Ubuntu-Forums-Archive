---
title: "Locked out - Authentication token manipulation error"
date: 2012-12-07
forum: General Help
---

### Post by Seventh7 on 2012-12-07
Hi folks,

I have a new Ubuntu 12 server install that I've just finished building and configuring. It's working correctly, but for some reason I can no longer log in as the system is rejecting my password. There's one account on the machine (labuser), and I'm 100% sure I'm not just typing the password incorrectly.

Here's what I've done so far:

I've followed [this method](http://www.psychocats.net/ubuntu/resetpassword) of booting into recovery mode, and then mounted the fs as read-write by using:

[I]mount -rw -o remount /
[/I]
I've confirmed that I can write to it by just touching a file. When I run 'passwd labuser' and enter the new password, I get:

[I]Sorry, passwords do not match
passwd: Authentication token manipulation error
passwd: passwd unchanged
[/I]

Again, I am definitely typing the password correctly. I did some googling and saw that /etc/shadow should be set to 000, so I chmod it, no change. 

I tried to get around it by just adding a new user and using that to log in with, but I get the exact same sequence of errors there as well, regardless if I run adduser as su or not.

I'm stumped! I really don't want to have to reinstall, as it took me about half a day to configure all of the services I'm using this for, but I'm at a loss here. Any insight would be awesome. 

Thanks!

---

### Post by SeijiSensei on 2012-12-07
You were on the right track but you had the wrong syntax for mount.  Try this:

```
mount -o remount,rw -n /
```

The -n tells mount not to try and write to /etc/mtab which is won't be able to do on a read-only filesystem.

I checked the linked article you cited, and it has the correct syntax. You must have just typed it wrong.

---

### Post by Seventh7 on 2012-12-07
> **SeijiSensei said:**
> You were on the right track but you had the wrong syntax for mount.  Try this:

```
mount -o remount,rw -n /
```

The -n tells mount not to try and write to /etc/mtab which is won't be able to do on a read-only filesystem.

I checked the linked article you cited, and it has the correct syntax. You must have just typed it wrong.

That didn't work either, unfortunately. Same error. :(

(Thank you for the quick reply, btw! :) )

---

### Post by steeldriver on 2012-12-07
... also I think you should revert the changes you made to /etc/shadow, afaik the correct permissions are

```
$ stat -c '%a' /etc/shadow
640

``````
$ ls -l /etc/shadow
-rw-r----- 1 root shadow 980 Nov 30 09:46 /etc/shadow

```

---

### Post by Seventh7 on 2012-12-07
I changed /etc/shadow to 640, and my permissions match those now. Same deal unfortunately.

It's odd that it's telling me that the passwords do not match. I'm typing as slowly and deliberately as I can, to the point where I'd be embarrassed if someone walked by and saw me, haha.

---

