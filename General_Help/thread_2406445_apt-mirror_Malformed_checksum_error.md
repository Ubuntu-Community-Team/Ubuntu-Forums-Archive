---
title: "apt-mirror Malformed checksum error"
date: 2018-11-21
forum: General Help
---

### Post by thexnightmare on 2018-11-21
Hello, I am trying to mirror ubuntu xenial repository by apt-mirror, but after running "sudo apt-mirror" I get Malformed checksum error, any idea how to fix it?
Downloading 1565 index files using 20 threads...
Begin time: Wed Nov 21 11:11:21 2018
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Wed Nov 21 11:11:51 2018


Malformed checksum line "3ccf81a9f9ec2a984fed5f6c687675178771f7ec  41054" in [http://archive.ubuntu.com/ubuntu/dists/xenial/main/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/xenial/main/i18n/Index) at /usr/bin/apt-mirror line 562, <STREAM> line 118.
Malformed checksum line "3ccf81a9f9ec2a984fed5f6c687675178771f7ec  41054" in [http://archive.ubuntu.com/ubuntu/dists/xenial/main/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/xenial/main/i18n/Index) at /usr/bin/apt-mirror line 562, <STREAM> line 12790.
Malformed checksum line "3ccf81a9f9ec2a984fed5f6c687675178771f7ec  41054" in [http://archive.ubuntu.com/ubuntu/dists/xenial/main/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/xenial/main/i18n/Index) at /usr/bin/apt-mirror line 562, <STREAM> line 12790.
Processing tranlation indexes: [TTTTTTTTTTTTTTT]

---

### Post by HermanAB on 2018-11-21
Hmm, that happens close to the beginning of the process.

Maybe try to slow things down with "set limit_rate 20k" or some such in "/etc/apt/mirror.lists" and try again.  

The apt-mirror script calls wget, so when things go wrong, you can kill and restart it and it will carry on where it left off.

---

### Post by thexnightmare on 2018-11-21
thx man, just tried, same results

---

### Post by HermanAB on 2018-11-21
I was updating my mirror in the UAE with bionic LTS and everything worked fine, but this morning IT complained about the bandwidth use, so I stopped it and will schedule it again over the weekend.

In general, apt-mirror is very robust, provided that you have sufficient bandwidth, so that wget doesn't time out and you have enough disk space, so that wget has somewhere to save the files.  When things go south, I just restart it again.

So, maybe reduce the threadcount to 1 and run tcpdump or wireshark to see what is happening.

---

