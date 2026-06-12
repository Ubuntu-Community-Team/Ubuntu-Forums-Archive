---
title: "Reading package lists... Error!"
date: 2013-04-19
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-04-19
Hello,

I got the following errors:

Reading package lists... Error!
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG D45DF2E8FC91AE7E Launchpad PPA for Geza Kovacs
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/debian.yacy.net_._en
E: The package lists or status file could not be parsed or opened.
sophie@sophie-Inspiron-5520:~$ 

Update Manager and Synaptic package manager show errors.  Should I remove and reinstall them?

Also, please see attachment.

Thanks Hannibal

---

### Post by oldos2er on 2013-04-19
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by coljohnhannibalsmith on 2013-04-19
I tried both methods.  Neither worked.  Please Help,  Hannibal

---

### Post by fantab on 2013-04-20
Try this:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

.. and tell us if it helped.

---

### Post by coljohnhannibalsmith on 2013-04-20
Yes this worked.

Thanks Hannibal

---

### Post by ibjsb4 on 2013-04-20
Just my own curiosity acting up, but why would one work and not the other?

```
sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

did not work, but ..

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

did work

---

### Post by coljohnhannibalsmith on 2013-04-20
Sorry,

No idea.

---

