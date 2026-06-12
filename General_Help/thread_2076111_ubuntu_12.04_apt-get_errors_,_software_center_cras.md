---
title: "ubuntu 12.04 apt-get errors , software center crash"
date: 2012-10-25
forum: General Help
---

### Post by irieites on 2012-10-25
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://mirror.ovh.net](http://mirror.ovh.net) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.ovh.net_ubuntu_dists_precise_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.



I got this error when running sudo apt-get update; im getting the same kind of error when trying apt-get install.
my software center is also crashing everytime i try to open it.
it tells me: could not determine the package or source package name.

help appreciated, thanks

---

### Post by dino99 on 2012-10-25
looks like ovh have made some change(s), so better to switch to "main" server instead.

---

### Post by jerrrys on 2012-10-25
BADSIG can be fixed:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en")
-------------------------------
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

Looks like a bad link, you could just uncheck it:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)
-------------------------------
E: The package lists or status file could not be parsed or opened.

In terminal:

sudo rm /var/lib/apt/lists/* -vf 

sudo apt-get update

---

### Post by irieites on 2012-10-25
that fixed it, thanks a lot!

---

### Post by jerrrys on 2012-10-25
Welcome  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

