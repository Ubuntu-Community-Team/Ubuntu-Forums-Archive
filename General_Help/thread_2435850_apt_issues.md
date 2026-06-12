---
title: "apt issues"
date: 2020-01-27
forum: General Help
---

### Post by dik232 on 2020-01-27
Having problems with apt today.  Trying the usual method to fix and it's not helping...

sudo apt-get update


```
Err:6 http://archive.ubuntu.com/ubuntu bionic InRelease
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
...
...
W: GPG error: http://archive.ubuntu.com/ubuntu bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
E: The repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32

```
/usr/bin/apt-key: 296: /usr/bin/apt-key: sort: not foundExecuting: /tmp/apt-key-gpghome.g9Rwm3W85K/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
gpg: key 3B4FE6ACC0B21F32: 20 signatures not checked due to missing keys
gpg: key 3B4FE6ACC0B21F32: public key "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
/usr/bin/apt-key: 296: /usr/bin/apt-key: sort: not found
/usr/bin/apt-key: 56: /usr/bin/apt-key: sort: not found
```

I've done a lot of searching but this is where I'm stuck.  I've tried keys.gnupg.net with the same result.

Any ideas?

---

### Post by dik232 on 2020-01-27
I have now tried Y PPA Manager's "Try to import all missing GPG keys" with no success

---

### Post by CelticWarrior on 2020-01-27
Change the server and try again.
Y PPA Manager is not for such cases.

---

### Post by dik232 on 2020-01-27
```
Err:6 http://gb.archive.ubuntu.com/ubuntu bionic InRelease              
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
```

Still getting the same error for key update

```
/usr/bin/apt-key: 296: /usr/bin/apt-key: sort: not foundExecuting: /tmp/apt-key-gpghome.GkGIVuQTZU/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
gpg: key 3B4FE6ACC0B21F32: 20 signatures not checked due to missing keys
gpg: key 3B4FE6ACC0B21F32: public key "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
/usr/bin/apt-key: 296: /usr/bin/apt-key: sort: not found
/usr/bin/apt-key: 56: /usr/bin/apt-key: sort: not found

```

---

### Post by CelticWarrior on 2020-01-27
Then try:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
```

and report back.

---

### Post by dik232 on 2020-01-27
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32

```
/usr/bin/apt-key: 296: /usr/bin/apt-key: sort: not foundExecuting: /tmp/apt-key-gpghome.JWnYqasZDq/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
gpg: key 3B4FE6ACC0B21F32: 20 signatures not checked due to missing keys
gpg: key 3B4FE6ACC0B21F32: public key "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
/usr/bin/apt-key: 296: /usr/bin/apt-key: sort: not found
/usr/bin/apt-key: 56: /usr/bin/apt-key: sort: not found

```

---

### Post by CelticWarrior on 2020-01-27
What Ubuntu flavor are you using? Please also post the results of ```
uname -a
```

---

### Post by dik232 on 2020-01-27
18.04 with default Ubuntu / Gnome desktop

Linux SG10 5.3.0-26-generic #28~18.04.1-Ubuntu SMP Wed Dec 18 16:40:14 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by CelticWarrior on 2020-01-27
So, everything looks fine.

I suggest you wait until tomorrow and then try again. This issues tend to resolve themselves.

---

### Post by dik232 on 2020-01-27
I will wait until tomorrow

I have another machine running 18.04 that doesn't have this problem.  Very odd

---

### Post by dik232 on 2020-01-28
It's now the next day and nothing has changed.

Anyone have any ideas?

---

### Post by dik232 on 2020-01-28
What does this mean?  I can't find anything online

```
[COLOR=#000000][FONT=&amp]/usr/bin/apt-key: 296: /usr/bin/apt-key: sort: not found[/FONT][/COLOR]
```

---

### Post by Holger_Gehrke on 2020-01-28
'apt-key' is a shell-script. Line 296 reads
```
for trusted in $(echo "$TRUSTEDPARTSLIST" | sort); do
```
so  it wants to sort the list of trusted keys from /etc/apt/trusted.gpg.d/ and then loop over the list and do something with these keys.
For some reason it can't find the program 'sort'. Since sort comes from  the package coreutils and should therefore be installed this is very,  very strange.
Check 'which sort' and perhaps 'locate sort' to see whether sort is installed. Use 'dpkg-query -l coreutils' to check the status of the coreutils package.

Holger

---

### Post by dik232 on 2020-01-28
dpkg-query -l coreutils

```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version             Architecture        Description
+++-=============================-===================-===================-===============================================================
ii  coreutils                     8.28-1ubuntu1       amd64               GNU core utilities


```

Exactly the same as my other 18.04 machine here

---

### Post by dik232 on 2020-01-28
I've now downloaded [coreutils_8.28-1ubuntu1_amd64.deb]("https://launchpad.net/ubuntu/+source/coreutils/8.28-1ubuntu1/+build/14251074") and dpkg -i and sudo apt-key adv now works.

Reinstalled coreutils using apt for good measure and everything's good to go

Thanks Holger, you're a star  :smile:

---

