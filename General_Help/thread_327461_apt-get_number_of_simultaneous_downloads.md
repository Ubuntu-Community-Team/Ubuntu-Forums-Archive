---
title: "apt-get number of simultaneous downloads"
date: 2006-12-29
forum: General Help
---

### Post by gazmon on 2006-12-29
Hello!
How can I set number of simultaneous downloads with apt-get?
I need set to single file because my 56k connection have many problem with more than 1 file.

---

### Post by anaconda on 2006-12-29
If I have understood apt-get correctly..

I think apt-get downloads 1 file at a time by default. I dont think it is even possible to download several files simultaneusly with apt-get..

---

### Post by bjornTFN on 2007-08-25
I have the same problem - apt-get downloads up to 3 files simultaneously but because my internet connection is slow (at best :-) ) 

apt keeps getting "connection reset by peer" in the middle of the download. 

Is there any way to change the maximum number of simultaneous downloads in apt, or possibly force it to retry those failed downloads?

I'm running Ubuntu 7.04, if that helps, and the connection is dialup (sad, but true).
Thanks guys

---

### Post by apetresc on 2007-08-25
You can use ```
apt-get -d install
``` to *only* download the .deb package, not install it; this should therefore allow you to circumvent the locking rule and have multiple sessions going at once (but I'm not sure, you should try).

At any rate, I think only Synaptic/Adept actually do simultaneous package downloads. The base apt-get tool doesn't as far as I can tell, so I recommend using that instead of the GUI.

---

### Post by bjornTFN on 2007-08-25
apt-get install -d Doesn't circumvent the locking rule, unfortunately. Worth a try though, heres a copy of the error in any case:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

So I guess it also locks the download directory.

Using -d and trying to download xubuntu (for example), gives me the same problem. Heres terminal output:

0 upgraded, 87 newly installed, 1 to remove and 0 not upgraded.
Need to get 61.9MB/61.9MB of archives.
After unpacking 234MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main vim-runtime 1:7.0-164+1ubuntu7.1
  Could not resolve 'security.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main abiword-common 2.4.6-1.1ubuntu2
  Could not resolve 'za.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main mozilla-thunderbird 1.5.0.13-0ubuntu0.7.04
  Could not resolve 'security.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main abiword 2.4.6-1.1ubuntu2
  Could not resolve 'za.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main xfce4-terminal 0.2.6-0ubuntu3.1
  Could not resolve 'security.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main libaiksaurus-1.2-data 1.2.1+dev-0.12-3build1
  Could not resolve 'za.archive.ubuntu.com'
0% [Connecting to security.ubuntu.com] [Connecting to za.archive.ubuntu.com]

And so on. Basically, apt (from the command line) tries to download the two [] items at once. If my dialup speed is decent it usually manages to connect one up and download, but the other fails, so essentially I miss a whole load of packages until the first package is done, then it connects one more package and spins through on the other again.

Thanks for the assist!

---

### Post by bjornTFN on 2007-08-25
Sorry, was being n00b, dialup has a habit of going down often. I reconnected, tried for Xubuntu-desktop again, Terminal output was:

Get:1 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main abiword-common 2.4.6-1.1ubuntu2 [1846kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main vim-runtime 1:7.0-164+1ubuntu7.1 [5210kB]
0% [2 vim-runtime 5477/5210kB 0%] [1 abiword-common 21720/1846kB 1%]

It sometimes connects both (like this) but because the connection is slow, only allows the one to download (abiword-common above). The other package waits for a few minutes and then gets closed by the remote server (supposedly because its inactive). 

I think apt initialises both (or sometimes three) downloads at once, and then downloads only one at a time, switching between them after a short while. So its not really simultaneuos, however, because the downloads are all initialised and the remote server sees no activity on some of them (because apt is downloading another), the remote server stops the inactive ones.

Hope the problem is a bit clearer :-)

Thanks again

---

