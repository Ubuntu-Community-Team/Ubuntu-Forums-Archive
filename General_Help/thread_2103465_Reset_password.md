---
title: "Reset password"
date: 2013-01-10
forum: General Help
---

### Post by ruwan2 on 2013-01-10
Hi,
I added an account to Ubuntu 12.1. It did not ask me for password. Then, it asked for password when I logged in for the first time.

Thus, I need to reset the password. This link gives a method to reset account password:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

First, I go to the recovery mode of Ubuntu.
Unfortunately, when I enter: "mount -o rw, remount /", it echoes:

mount: special device remount does not exist

So, what is the problem to reset the password.

Thanks,

---

### Post by coffeecat on 2013-01-10
> **ruwan2 said:**
> Unfortunately, when I enter: "mount -o rw, remount /", it echoes:

mount: special device remount does not exist

There should be no space between the comma and remount. This is the command you need:

```
mount -o rw,remount /
```

> **ruwan2 said:**
> I added an account to Ubuntu 12.1. It did not ask me for password.

Please elaborate. How did you add the account, or do you mean that you made a fresh installation?

---

### Post by sudodus on 2013-01-10
> **ruwan2 said:**
> Hi,
I added an account to Ubuntu 12.1. It did not ask me for password. Then, it asked for password when I logged in for the first time.

Thus, I need to reset the password. This link gives a method to reset account password:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

First, I go to the recovery mode of Ubuntu.
Unfortunately, when I enter: "mount -o [COLOR="Red"]rw, remoun[/COLOR]t /", it echoes:

mount: special device remount does not exist

So, what is the problem to reset the password.

Thanks,
There should be no space between ',' and 'remount'.

Otherwise, if this is a new account and you have an old one that works, log into the working one and use

```
users-admin
```

or according to psychocats (but directly)
```
sudo passwd 'username'
```

---

### Post by tp21 on 2013-06-10
hi, i have the same problem.
i have thinkpad t61, with ubuntu 13.04.
i forgot my admint password, and i am trying to reset my password.
when i login to root prompt, and try to remount the file system through mount -o rw, remount / i receive this error: special device remount does not exist.
thanks

---

### Post by sum1nil on 2013-06-10
Try "sudo mount -t auto -o rw,remount /dev/sdXX  / " where sdXX is the drive and partition of your root volume. 
If you type "mount" by itself then hopefully root i.e. '/' will show up in the list of mounts.
For example, my root volume is on my second hard drive at partition 5 so I would use sdb5.

Edit: Ah, no sudo needed in recovery mode.

---

### Post by steeldriver on 2013-06-10
> **tp21 said:**
> when i login to root prompt, and try to remount the file system through [COLOR=#ff0000]mount -o rw, remount /[/COLOR] i receive this error: special device remount does not exist.
thanks

It looks like you are making the same mistake as the earlier posters - you need to remove the space between rw, and remount i.e. 

```
mount -o rw**,**remount /
```

Otherwise the 'mount' command sees 'remount' as the target device (instead of / ) rather than as a second option

---

### Post by tp21 on 2013-06-11
thanks a lot for your help.
i tried without space after the comma, with no luck. 
i didn't try sum1nil method.
anyways, i managed at the end to log in after i found my admin password written somewhere.
i just think that the reason why the recovery mode didn't work might be that the hard desk is encrypted. 
best

---

### Post by sudodus on 2013-06-11
> **tp21 said:**
> thanks a lot for your help.
i tried without space after the comma, with no luck. 
i didn't try sum1nil method.
anyways, i managed at the end to log in after i found my admin password written somewhere.
i just think that the reason why the recovery mode didn't work might be that the hard desk is encrypted. 
best

If the methods to reset passwords would work with encrypted home, the encryption would be useless. So you are right, it does not work with encryption.

---

