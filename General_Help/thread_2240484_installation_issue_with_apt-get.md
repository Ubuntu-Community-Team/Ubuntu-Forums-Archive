---
title: "installation issue with apt-get"
date: 2014-08-20
forum: General Help
---

### Post by heinrich2 on 2014-08-20
Hey,

I am currently running into an issue with: sudo apt-get install openssh-server. I am running ubuntu 12.10 in virtual box (on windows 8.1). Seems like it could be a repository issue, could someone point me into the right direction?

I have tried sudo apt-get update several times and my server is selected as the main one.

Here what i am getting:

user@user-VirtualBox:~$ sudo apt-get install openssh-server openssh-client
Reading package lists... Done
Building dependency tree 
Reading state information... Done
openssh-client is already the newest version.
The following extra packages will be installed:
ncurses-term ssh-import-id
Suggested packages:
rssh molly-guard openssh-blacklist openssh-blacklist-extra monkeysphere
The following NEW packages will be installed:
ncurses-term openssh-server ssh-import-id
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 775 kB of archives.
After this operation, 3,066 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
ncurses-term openssh-server ssh-import-id
Install these packages without verification [y/N]? Y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main ncurses-term all 5.9-10ubuntu1
404 Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main openssh-server i386 1:6.0p1-3ubuntu1
404 Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main ssh-import-id all 2.12-0ubuntu1
404 Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/ncurses-term_5.9-10ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/ncurses-term_5.9-10ubuntu1_all.deb) 404 Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_6.0p1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_6.0p1-3ubuntu1_i386.deb) 404 Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/ssh-import-id/ssh-import-id_2.12-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/ssh-import-id/ssh-import-id_2.12-0ubuntu1_all.deb) 404 Not Found [IP: 91.189.92.201 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Thank you for your help in advanced.

---

### Post by yancek on 2014-08-20
Support for Ubuntu 12.10 ended in May of this year so the repositories are no longer available.  12.04 and 14.04 are still supported.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by overdrank on 2014-08-20
Hi and welcome, one issue maybe that 12.10 has reached [_End of Life_]("https://wiki.ubuntu.com/Releases").

---

### Post by heinrich2 on 2014-08-20
So is there any workaround? Any way to do what I am trying with this version of Ubuntu (install SSH server)? Should i change software sources or sources.list?

Or is my only choice a different version of Ubuntu?

btw i have already had similar issues with installing other things like lzo and java, but managed to workaround with manual downloads. In this case nothing is working so far.

---

### Post by grahammechanical on 2014-08-20
It will be most difficult upgrading 12.10 because you can only upgrade to the next release and that was 13.04 and that also has reached end of life. But you can redirect apt-get to go to the new location of the 12.10 repositories. This wiki page shows what you have to do.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

In your case you still keep the quantal bit of the address. It this the old-release.ubuntu.com that you have to use to replace the existing repositories.

Regards.

---

