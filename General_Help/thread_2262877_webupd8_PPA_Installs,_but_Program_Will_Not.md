---
title: "webupd8 PPA Installs, but Program Will Not"
date: 2015-01-27
forum: General Help
---

### Post by ceil210 on 2015-01-27
I am trying to instal. fbmessenger which reuqires the webupd8 PPA.  I enter

```
sudo add-apt-repository ppa:nilarimogard/webupd8 

```
and my result is
```

 More info: https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpclqbi79m/secring.gpg' created
gpg: keyring `/tmp/tmpclqbi79m/pubring.gpg' created
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpclqbi79m/trustdb.gpg: trustdb created
gpg: key 4C9D234C: public key "Launchpad webupd8" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```

Seems normal enough.  apt-get update works as well!  Here is where the problem comes in.
```

sudo apt-get install fbmessenger

```

**This** yields 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fbmessenger
```



Help? :(

---

### Post by QIII on 2015-01-27
Hello!

You need to update your sources first.

```
sudo apt-get update
```

then install.

---

### Post by ceil210 on 2015-01-27
I did that already :(

---

### Post by QIII on 2015-01-27
Which release of Ubuntu are you using?

---

### Post by ceil210 on 2015-01-27
> **qiii said:**
> which release of ubuntu are you using?

14.04lts

---

### Post by QIII on 2015-01-27
OK.  I wasn't being obtuse, but making a point.  :)

Did you see this part from the instructions:

> To make it easier to install Facebook Messenger in Ubuntu 13.10, 13.04, 12.10 and 12.04, I've uploaded the application to the main WebUpd8 PPA. ?

There probably is not a candidate for 14.04 in the PPA.

---

### Post by ceil210 on 2015-01-27
Then what would you reccomend as a FB client?  Pidgin?

---

### Post by QIII on 2015-01-27
First, you might as well get rid of the PPA...

```
sudo apt-get install ppa-purge
```
```
sudo ppa-purge ppa:nilarimogard/webupd8
```

I don't use FB, so I really couldn't recommend anything.  Hang tight.  Someone will probably come along shortly with a good idea.

Cheers!

---

