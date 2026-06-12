---
title: "No pubkey found"
date: 2013-08-23
forum: General Help
---

### Post by satimis on 2013-08-23
Hi all,

Ubuntu 12.04 desktop 64bit

I was following;
Create a radio station in five minutes with Airtime 2.0 on Ubuntu or Debian
[http://www.freesoftwaremagazine.com/articles/create_radio_station_five_minutes_airtime_20_ubuntu_or_debian](http://www.freesoftwaremagazine.com/articles/create_radio_station_five_minutes_airtime_20_ubuntu_or_debian)

to install Airtime

Adding;
deb [http://apt.sourcefabric.org/](http://apt.sourcefabric.org/) precise main
on /etc/apt/sources.list

multiverse repository for MP3 encoding support, such as for precise:
alrady enabled
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise multiverse


Ran sudo apt-get update```

Reading package lists... Done
W: GPG error: http://apt.sourcefabric.org precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0888FE5B174C1854

```


sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0888FE5B174C1854```

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.KKunSUXuQX --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv 0888FE5B174C1854
gpg: requesting key 174C1854 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: No such file or directory
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

Please help.  TIA


B.R.
satimis

---

### Post by oldos2er on 2013-08-23
Have you tried switching to the main server?

---

### Post by satimis on 2013-08-23
> **oldos2er said:**
> Have you tried switching to the main server?
Hi,

Which main server?  Thanks

I have tried following servers without result'

keyserver hkp://subkeys.pgp.net
keyserver hkp://pgp.mit.edu
keyserver hkp://keys.nayr.net
keyserver [http://keys.gnupg.net](http://keys.gnupg.net)
hkp://pool.sks-keyservers.net

Rgds
satimis

---

### Post by oldos2er on 2013-08-24
I think I've misunderstood your original question, please forgive me.

A bit of googling shows me [this key]("http://yum.sourcefabric.org/RPM-GPG-KEY") which I believe is the one you're looking for.

---

### Post by satimis on 2013-08-24
> **oldos2er said:**
> I think I've misunderstood your original question, please forgive me.

A bit of googling shows me [this key]("http://yum.sourcefabric.org/RPM-GPG-KEY") which I believe is the one you're looking for.
Hi,

Thanks.  Kindly advise how to add it to /etc/apt/sources.lst

Rgds
satimis

---

### Post by sandyd on 2013-08-24
```

wget http://yum.sourcefabric.org/RPM-GPG-KEY
gpg --import RPM-GPG-KEY
gpg -a --export 174C1854 | sudo apt-key add -

```

---

### Post by satimis on 2013-08-26
> **sandyd said:**
> ```

wget http://yum.sourcefabric.org/RPM-GPG-KEY
gpg --import RPM-GPG-KEY
gpg -a --export 174C1854 | sudo apt-key add -

```
Hi,

Thanks for your advice.

Performed following steps:-
$ wget [http://yum.sourcefabric.org/RPM-GPG-KEY](http://yum.sourcefabric.org/RPM-GPG-KEY)```

--2013-08-25 07:43:13--  http://yum.sourcefabric.org/RPM-GPG-KEY
Resolving yum.sourcefabric.org (yum.sourcefabric.org)... 5.9.154.18
Connecting to yum.sourcefabric.org (yum.sourcefabric.org)|5.9.154.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1825 (1.8K)
Saving to: `RPM-GPG-KEY'

100%[======================================>] 1,825       --.-K/s   in 0.003s  

```

$ gpg --import RPM-GPG-KEY```

gpg: directory `/home/satimis/.gnupg' created
gpg: new configuration file `/home/satimis/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/satimis/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/satimis/.gnupg/secring.gpg' created
gpg: keyring `/home/satimis/.gnupg/pubring.gpg' created
gpg: /home/satimis/.gnupg/trustdb.gpg: trustdb created
gpg: key 174C1854: public key "Sourcefabric <contact@sourcefabric.org>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
gpg: no ultimately trusted keys found

```

$ sudo gpg --import RPM-GPG-KEY
[sudo] password for satimis: ```

gpg: WARNING: unsafe ownership on configuration file `/home/satimis/.gnupg/gpg.conf'
gpg: key 174C1854: "Sourcefabric <contact@sourcefabric.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

$ gpg -a --export 174C1854 | sudo apt-key add -```

OK

```

apt-get update is now working.


Rgds
satimis

---

