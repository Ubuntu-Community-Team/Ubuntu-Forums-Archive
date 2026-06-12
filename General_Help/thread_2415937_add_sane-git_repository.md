---
title: "add sane-git repository"
date: 2019-04-03
forum: General Help
---

### Post by pedro_rodriguez2 on 2019-04-03
I just added the sane-git repository, but it is disabled by default. How do I get it going on Ubuntu 18.04?

I get: 403  Forbidden [IP: 91.189.95.83 80]

Works fine on my laptop, but I added the repository a long time ago.

 >    
                                                 pedro@pedroschooloffice:~$ sudo add-apt-repository ppa:rolfbensch/sane-git
 Ubuntu SANE packages from SANE daily git snapshots ([http://www.sane-project.org/snapshots/](http://www.sane-project.org/snapshots/)).

Unchanged SANE daily git snapshots are ignored!

Please send scanner related questions to the SANE mailing list <email address hidden>.

If you need the last released scanner driver, you can use my other PPA: [https://launchpad.net/~rolfbensch/+a...u/sane-release]("https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-release").
 More info: [https://launchpad.net/~rolfbensch/+a...buntu/sane-git]("https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git")
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease   
Hit:2 [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) bionic InRelease               
Err:3 [http://ppa.launchpad.net/rolfbensch/ppa/ubuntu](http://ppa.launchpad.net/rolfbensch/ppa/ubuntu) bionic InRelease    
  403  Forbidden [IP: 91.189.95.83 80]
Hit:4 [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) bionic-updates InRelease       
Hit:5 [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) bionic-backports InRelease                                
Hit:6 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) bionic InRelease
Hit:7 [http://ppa.launchpad.net/rolfbensch/sane-git/ubuntu](http://ppa.launchpad.net/rolfbensch/sane-git/ubuntu) bionic InRelease    
Reading package lists... Done
E: Failed to fetch [http://ppa.launchpad.net/rolfbensch/...onic/InRelease]("http://ppa.launchpad.net/rolfbensch/ppa/ubuntu/dists/bionic/InRelease")  403  Forbidden [IP: 91.189.95.83 80]
E: The repository 'http://ppa.launchpad.net/rolfbensch/ppa/ubuntu bionic InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
pedro@pedroschooloffice:~$

---

