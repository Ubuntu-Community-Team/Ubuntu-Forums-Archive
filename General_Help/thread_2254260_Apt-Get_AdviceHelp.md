---
title: "Apt-Get Advice/Help"
date: 2014-11-25
forum: General Help
---

### Post by baudrillard on 2014-11-25
Hello there, I'm still teaching myself the more basic parts of Ubuntu, one being the whole "apt-get" procedure on terminal. 

 I just wanted to know if anyone knew a simple resource (and could post it) in regards to apt-get, something that explains it, where can I find a lot of apt-get commands for major software, etc.  

Additionally, any resources that would teach me how to handle tar.gz files, because I honestly have no clue how to use those. 

 Bonus points: Apt-get for Pycharm installation? Like I mentioned above, I have the tar.gz file, but I have no clue what to do with it. I feel that if I had the apt-get command, I'd be a lot better off.  

I understand these resources are out floating on the internet, but I came here hoping for a particularly good video/pdf/website that gives a good explanation for beginners.

Thank you.

---

### Post by carl4926 on 2014-11-26
man apt

There are online resources if you search

tar.gz are archive files, like a .zip
you extract the file to get to the contents
Usually a package archive will also contain install instructions

---

### Post by coldcritter64 on 2014-11-26
apt-get info link : [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

tar.gz are source code compressed files, not for use with apt-get. apt-get downloads and installs ".deb" files from a repository for installations, you are looking at files for source code installations with the tar.gz files.

 There is a getdeb repository with that program "pycharm" in it. [http://www.getdeb.net/software/pycharm](http://www.getdeb.net/software/pycharm) see if that is easier to use/suits better, than source code methods.

Another installation guide (also add the "getdeb" repo) : [http://www.thornstrom.net/how-to/linux/ubuntu-and-pycharm/](http://www.thornstrom.net/how-to/linux/ubuntu-and-pycharm/)

---

### Post by baudrillard on 2014-11-26
Thank you, Coldcritter64, the links for the apt-get resources were what I needed!

---

