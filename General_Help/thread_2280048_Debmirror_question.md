---
title: "Debmirror question"
date: 2015-05-27
forum: General Help
---

### Post by mfattahian on 2015-05-27
Hi Folks,


We’ve setup a local repository in our environment. Using “debmirror”


Seems it downloads a partial of Ubuntu. How can I get the most recent packages with this?


Here is the script:


**debmirror -a amd64 --no-source -s main,main/debian-installer,restricted,universe,multiverse -h ca.archive.ubuntu.com -d trusty,trusty-security,trusty-updates,trusty-backports /srv/repos/ubuntu-repo**

When I compare content of folders it's not match. For example


**[http://ca.archive.ubuntu.com/ubuntu/pool/main/a/acl/](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/acl/) has :**

**libacl1_2.2.52-2_amd64.deb**

**[http://ubuntu-repo/pool/main/a/acl/](http://ubuntu-repo/pool/main/a/acl/) doesn't have this and the last file is :**

**libacl1_2.2.52-1_amd64.deb**




Thanks for any help,


Mohammad

---

### Post by ian-weisser on 2015-05-28
```
$ rmadison acl
 acl | 2.2.51-5ubuntu1 | precise                  | source, amd64, armel, armhf, i386, powerpc
[COLOR=#ff0000]** acl | 2.2.52-1        | trusty                   | source, amd64, arm64, armhf, i386, powerpc, ppc64el**[/COLOR]
 acl | 2.2.52-1        | ubuntu-rtm/14.09         | source, amd64, armhf, i386
 acl | 2.2.52-1        | ubuntu-rtm/14.09-factory | source, amd64, armhf, i386
 acl | 2.2.52-1.1      | utopic                   | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 acl | 2.2.52-2        | vivid                    | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 acl | 2.2.52-2        | wily                     | source, amd64, arm64, armhf, i386, powerpc, ppc64el
```

Your debmirror is right.
Newer versions in the pool are for newer versions of Ubuntu.

 Apt uses [http://ca.archive.ubuntu.com/ubuntu/dists/[COLOR=#ff0000]**trusty**[/COLOR]/main/source/sources.bz2]("http://ca.archive.ubuntu.com/ubuntu/dists/trusty/main/source/sources.bz2") to determine which pool file is appropriate for your release of Ubuntu.

---

