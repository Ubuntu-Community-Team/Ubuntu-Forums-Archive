---
title: "unable to run sudo apt-get upgrade using ubuntu 16.04.3 LTS"
date: 2017-12-02
forum: General Help
---

### Post by sic698 on 2017-12-02
Hi, I am unable to run sudo  apt-get upgrade using  ubuntu 16.04.3 lts, I receive the following error The package systemd  needs to be reinstalled, but I can't find an archive for it.

---

### Post by deadflowr on 2017-12-02
Re-run the command
(but first run
```
sudo apt-get update
```
)
and then copy the output and post it in code tags;
(Click on Reply to Thread and then click on the # symbol to set code tags)

---

### Post by sic698 on 2017-12-02
[LIST=1]
[*][INDENT]```
:~$ sudo apt-get update
Hit:1 [http://ppa.launchpad.net/freetuxtv/freetuxtv-dev/ubuntu](http://ppa.launchpad.net/freetuxtv/freetuxtv-dev/ubuntu) xenial InRelease
Hit:2 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:3 [http://repo.acestream.org/ubuntu](http://repo.acestream.org/ubuntu) trusty InRelease                                                                    
Hit:4 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-security  InRelease                                                       
Hit:5 [http://ppa.launchpad.net/hda-me/xscreensaver/ubuntu](http://ppa.launchpad.net/hda-me/xscreensaver/ubuntu) xenial InRelease                         
Hit:6 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates InRelease       
Err:3 [http://repo.acestream.org/ubuntu](http://repo.acestream.org/ubuntu) trusty InRelease                       
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 50E2BCF0E3805CD8
Hit:7 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-proposed InRelease                                 
Hit:8 [http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu](http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu) xenial InRelease                          
Hit:9 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-backports InRelease    
Hit:10 [http://ppa.launchpad.net/purplei2p/i2pd/ubuntu](http://ppa.launchpad.net/purplei2p/i2pd/ubuntu) xenial InRelease       
Hit:11 [http://ppa.launchpad.net/trebelnik-stefina/tv-maxe/ubuntu](http://ppa.launchpad.net/trebelnik-stefina/tv-maxe/ubuntu) xenial InRelease
Reading package lists... Done                       
W:  [http://ppa.launchpad.net/freetuxtv/freetuxtv-dev/ubuntu/dists/xenial/InRelease:](http://ppa.launchpad.net/freetuxtv/freetuxtv-dev/ubuntu/dists/xenial/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg  are  ignored as the file is not readable by user '_apt' executing  apt-key.
W:  [http://ca.archive.ubuntu.com/ubuntu/dists/xenial/InRelease:](http://ca.archive.ubuntu.com/ubuntu/dists/xenial/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg are   ignored as the file is not readable by user '_apt' executing apt-key.
W: [http://repo.acestream.org/ubuntu/dists/trusty/InRelease:](http://repo.acestream.org/ubuntu/dists/trusty/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg are   ignored as the file is not readable by user '_apt' executing apt-key.
W: An error occurred during the signature verification. The repository   is not updated and the previous index files will be used. GPG error:  [http://repo.acestream.org/ubuntu](http://repo.acestream.org/ubuntu)  trusty InRelease: The  following signatures couldn't be verified because  the public key is not  available: NO_PUBKEY 50E2BCF0E3805CD8
W:  [http://ca.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease:](http://ca.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg  are  ignored as the file is not readable by user '_apt' executing  apt-key.
W:  [http://ppa.launchpad.net/hda-me/xscreensaver/ubuntu/dists/xenial/InRelease:](http://ppa.launchpad.net/hda-me/xscreensaver/ubuntu/dists/xenial/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg  are  ignored as the file is not readable by user '_apt' executing  apt-key.
W:  [http://ca.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease:](http://ca.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg  are  ignored as the file is not readable by user '_apt' executing  apt-key.
W:  [http://ca.archive.ubuntu.com/ubuntu/dists/xenial-proposed/InRelease:](http://ca.archive.ubuntu.com/ubuntu/dists/xenial-proposed/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg  are  ignored as the file is not readable by user '_apt' executing  apt-key.
W:  [http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu/dists/xenial/InRelease:](http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu/dists/xenial/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg  are  ignored as the file is not readable by user '_apt' executing  apt-key.
W:  [http://ca.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease:](http://ca.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg  are  ignored as the file is not readable by user '_apt' executing  apt-key.
W:  [http://ppa.launchpad.net/purplei2p/i2pd/ubuntu/dists/xenial/InRelease:](http://ppa.launchpad.net/purplei2p/i2pd/ubuntu/dists/xenial/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg  are  ignored as the file is not readable by user '_apt' executing  apt-key.
W:  [http://ppa.launchpad.net/trebelnik-stefina/tv-maxe/ubuntu/dists/xenial/InRelease:](http://ppa.launchpad.net/trebelnik-stefina/tv-maxe/ubuntu/dists/xenial/InRelease:)   The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg  are  ignored as the file is not readable by user '_apt' executing  apt-key.
W: Failed to fetch  [http://repo.acestream.org/ubuntu/dists/trusty/InRelease](http://repo.acestream.org/ubuntu/dists/trusty/InRelease)  The  following signatures couldn't be verified because the public key is not  available: NO_PUBKEY 50E2BCF0E3805CD8
W: Some index files failed to download. They have been ignored, or old ones used instead.


this is what I get when I run sudo-apt get update
```[/INDENT]
 
[/LIST]

---

### Post by deadflowr on 2017-12-02
See if running
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 50E2BCF0E3805CD8
sudo apt-get update
```
fixes the acestream key problem.

Not sure what the Warning about the jockey-drivers.gpg keys is about, though.
Seems like the file has a permissions issues
What does
```
ls -la /etc/apt/trusted.gpg.d/jockey-drivers.gpg
```
show?
(also double check my spelling there)

---

### Post by oldos2er on 2017-12-02
W: Failed to fetch [http://repo.acestream.org/ubuntu/dists/trusty/InRelease](http://repo.acestream.org/ubuntu/dists/trusty/InRelease) That repo should be disabled since it's for trusty, and you're running Xenial.

@sic698 Why did you remove post #3? People will need that information to help you.

---

### Post by sic698 on 2017-12-02
Sorry i lost mis-typed something and lost everything and cant get the post from previous post 3, seems like your solutions seemed to have fixed my updates and upgrades. thanks.

---

