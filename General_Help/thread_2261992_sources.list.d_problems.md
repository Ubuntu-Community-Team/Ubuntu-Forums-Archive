---
title: "sources.list.d problems"
date: 2015-01-22
forum: General Help
---

### Post by zkab on 2015-01-22
I have Ubuntu server 14.04 and trying to install software oscam.
According to instructions I should start with:

sudo apt-add-repository ppa:oscam/ppa
sudo apt-get update

This is what I got after that:
-----------------------------------
[email]rajan@tv-server:/etc/apt/sources.list[/email].d$ ls -la
total 12
drwxr-xr-x 2 root root 4096 Jan 22 17:16 .
drwxr-xr-x 6 root root 4096 Jan 19 18:07 ..
-rw-r--r-- 1 root root  122 Jan 22 17:16 oscam-ppa-trusty.list
[email]rajan@tv-server:/etc/apt/sources.list[/email].d$ cat oscam-ppa-trusty.list 
deb [http://ppa.launchpad.net/oscam/ppa/ubuntu](http://ppa.launchpad.net/oscam/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/oscam/ppa/ubuntu](http://ppa.launchpad.net/oscam/ppa/ubuntu) trusty main
-----------------------------------
rajan@tv-server:~$ apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   2048R/5E12C7CF 2013-03-27
uid                  Tvheadend (Package Signing Key) <apt@tvheadend.org>
sub   2048R/0C908981 2013-03-27

/etc/apt/trusted.gpg.d/oscam-ppa.gpg
------------------------------------
pub   1024R/BDBE1D1E 2011-08-28
uid                  Launchpad PPA for OSCam
-----------------------------------
Then oscam is ready to installed with 'sudo apt-get install oscam'
But I get following:
-----------------------------------
rajan@tv-server:~$ sudo apt-get install oscam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package oscam
-----------------------------------
I thought that /etc/apt/sources.list.d contained additional lines to /etc/apt/sources.list but somehow sudo apt-get install oscam can't pick up that ...

---

### Post by Doug S on 2015-01-22
> **zkab said:**
> I have Ubuntu [COLOR=#ff0000]server[/COLOR] 14.04 and trying to install software oscam.I have not had success using the normal instructions with a server. However, I have if I use the "old fashioned method". There is a pretty good reference [here]("http://askubuntu.com/questions/38021/how-to-add-a-ppa-on-a-server") (scroll down to the "old fashioned method"). Just a few days ago, I also wrote notes for myself [here]("http://www.smythies.com/~doug/linux/ppa/index.html") (while you have no reason to take my word for it, my web site is safe).

Edit: Ignore my post, the correct answer, package name (which I completely missed when I checked out the ppa page), is in the below two posts.

---

### Post by CantankRus on 2015-01-22
The last stable release appears to be for Lucid.
From that ppa isn't the package you want **oscam-svn**

Have a look at [https://launchpad.net/~oscam/+archive/ubuntu/ppa/+packages](https://launchpad.net/~oscam/+archive/ubuntu/ppa/+packages)

---

### Post by papibe on 2015-01-22
Hi zkab.

If you go the ppa page [here]("https://launchpad.net/~oscam/+archive/ubuntu/ppa"), and then filter the packages available for trusty, you'll see that the package is called oscam-svn.

With that in mind, you should be able to install it by running:
```
sudo apt-get install oscam-svn
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by zkab on 2015-01-23
Thanks for all help - installation went just fine.
Now is the challenge to get it work ...

---

### Post by Bashing-om on 2015-01-23
zkab; Hello;

Great, glad ya got it whooped .

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on
[INDENT][INDENT][INDENT]keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

