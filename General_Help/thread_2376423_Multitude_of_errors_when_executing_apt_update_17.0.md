---
title: "Multitude of errors when executing apt update 17.04"
date: 2017-11-02
forum: General Help
---

### Post by mblahay on 2017-11-02
I'm not sure where to start here, so I am posting the entire output. apt upgrade does not do anything, and I suspect that is because I cannot pull down updated repository information. I'm not a new Ubuntu user, but I really don't know much about the management of repositories.```
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty InRelease [243 kB]  

Get:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [1,189 B]           
Get:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty InRelease [10.2 kB]            

Ign:5 [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) zesty InRelease               
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease [89.2 kB]     
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates InRelease [89.2 kB]    
Ign:8 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable InRelease                      
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports InRelease [89.2 kB]
Get:10 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release [2,709 B]             
Get:11 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release.gpg [819 B]           
Err:13 [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) zesty Release                
  404  Not Found
Err:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Err:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Ign:14 [https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh](https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh) trusty-cdh5 InRelease
Err:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Ign:15 [https://dl.bintray.com/sbt/debian](https://dl.bintray.com/sbt/debian)  InRelease
Get:16 [https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh](https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh) trusty-cdh5 Release [1,686 B]
Get:17 [https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh](https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh) trusty-cdh5 Release.gpg [198 B]
Get:18 [https://dl.bintray.com/sbt/debian](https://dl.bintray.com/sbt/debian)  Release [815 B]
Ign:11 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release.gpg  
Get:19 [https://dl.bintray.com/sbt/debian](https://dl.bintray.com/sbt/debian)  Release.gpg [821 B]
Err:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Ign:17 [https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh](https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh) trusty-cdh5 Release.gpg
Err:20 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Ign:19 [https://dl.bintray.com/sbt/debian](https://dl.bintray.com/sbt/debian)  Release.gpg
Reading package lists... Done 
E: The repository 'http://ppa.launchpad.net/midori/ppa/ubuntu zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2CC26F777B8B44A1
E: The repository 'http://repo.vivaldi.com/stable/deb stable Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh](https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh) trusty-cdh5 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 327574EE02A818DD
E: The repository 'https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh trusty-cdh5 Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [https://dl.bintray.com/sbt/debian](https://dl.bintray.com/sbt/debian)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 99E82A75642AC823
E: The repository 'https://dl.bintray.com/sbt/debian  Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by vasa1 on 2017-11-02
Please post the output of```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```and please don't format the output using [noparse][INDENT][/noparse] and [noparse][/INDENT][/noparse] :)

---

### Post by mblahay on 2017-11-02
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty-updates main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty-updates universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty-updates multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse
/etc/apt/sources.list.d/cloudera-cdh5.list:deb [arch=amd64] [https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh](https://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh) trusty-cdh5 contrib
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/midori-ubuntu-ppa-zesty.list:deb [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) zesty main
/etc/apt/sources.list.d/opera-stable.list:deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/sbt.list:deb [https://dl.bintray.com/sbt/debian](https://dl.bintray.com/sbt/debian) /
/etc/apt/sources.list.d/vivaldi.list:deb [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main

---

### Post by ian-weisser on 2017-11-02
You have a couple different types of errors there:

Here's one:

```
Err:13 http://ppa.launchpad.net/midori/ppa/ubuntu zesty Release                
  404  Not Found
```

404 meant the same thing in apt is it does everywhere else. Go ahead, try to open that URL in a web browser.
If an URL does not exists, delete it from your sources.


Here's another:

```
Err:4 http://archive.canonical.com/ubuntu zesty InRelease
```
This is answered thoroughly at [https://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey](https://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey)

---

### Post by mblahay on 2017-11-06
I was able to get rid of the 404 error by commenting out the midori ppa entry.

As for the errors involving the NO_PUBKEY message, I'm not able to make progress. 
[FONT=courier new]
[/FONT][FONT=courier new]sudo -E apt-key adv --keyserver-options http-proxy=http://localhost:3128  --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32[/FONT]
[FONT=courier new]Executing: /tmp/apt-key-gpghome.DXhPrgWO3L/gpg.1.sh --keyserver-options http-proxy=http://localhost:3128 --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32[/FONT]
[FONT=courier new]gpg: [don't know]: invalid packet (ctb=00)[/FONT]
[FONT=courier new]gpg: keydb_get_keyblock failed: Value not found[/FONT]
[FONT=courier new]gpg: [don't know]: invalid packet (ctb=00)[/FONT]
[FONT=courier new]gpg: /tmp/apt-key-gpghome.DXhPrgWO3L/pubring.gpg: copy to '/tmp/apt-key-gpghome.DXhPrgWO3L/pubring.gpg.tmp' failed: Invalid packet[/FONT]
[FONT=courier new]gpg: error writing keyring '/tmp/apt-key-gpghome.DXhPrgWO3L/pubring.gpg': Invalid packet[/FONT]
[FONT=courier new]gpg: [don't know]: invalid packet (ctb=00)[/FONT]
[FONT=courier new]gpg: keydb_search failed: Invalid packet[/FONT]
[FONT=courier new]gpg: key 3B4FE6ACC0B21F32: public key "[User ID not found]" imported[/FONT]
[FONT=courier new]gpg: [don't know]: invalid packet (ctb=00)[/FONT]
[FONT=courier new]gpg: error reading '[stream]': Invalid packet[/FONT]
[FONT=courier new]gpg: Total number processed: 0[/FONT]
[FONT=courier new]gpg:               imported: 1[/FONT]

---

### Post by mblahay on 2017-11-13
Is there possibly a problem with my being behind a proxy when I do this?

---

