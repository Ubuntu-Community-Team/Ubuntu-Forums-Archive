---
title: "Invalid Signature Help"
date: 2014-05-22
forum: General Help
---

### Post by Random_Pinenut_Joy on 2014-05-22
I keep coming up with this error when updating my system.

W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Any help would be appreciated. I Have tried;

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5

With the result of;

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.NXfm2Ca8hB --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/atareao-atareao.gpg --keyring /etc/apt/trusted.gpg.d/ingalex-super-boot-manager.gpg --keyring /etc/apt/trusted.gpg.d/mc3man-trusty-media.gpg --keyring /etc/apt/trusted.gpg.d/nilarimogard-webupd8.gpg --keyring /etc/apt/trusted.gpg.d/noobslab-apps.gpg --keyring /etc/apt/trusted.gpg.d/noobslab-indicators.gpg --keyring /etc/apt/trusted.gpg.d/ravefinity-project-ppa.gpg --keyring /etc/apt/trusted.gpg.d/tualatrix-next.gpg --keyring /etc/apt/trusted.gpg.d/ubuntu-wine-ppa.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-java.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 26 new signatures
gpg: Total number processed: 1
gpg:         new signatures: 26

Then 'apt-get update' with a return of invalid signature again.

---

### Post by ibjsb4 on 2014-05-23
Create a new /var/lib/apt/list or ..

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Random_Pinenut_Joy on 2014-05-23
Thank You so very much, I couldn't remember how the commands ran.
All fixed and updating.

---

### Post by ibjsb4 on 2014-05-23
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

