---
title: "Installed wrong version of libpcap and can't get the right one back"
date: 2014-09-12
forum: General Help
---

### Post by ediblestarling on 2014-09-12
In playing around with some wireless network auditing tools I ran into a problem that told me to try and use a previous version of libpcap. In a rookie move I tried to install both the 64 bit and the i386 versions...and older versions at that. Didn't work correctly, and now I can't seem to get the proper version restored. I tried to start by uninstalling Wireshark, and here's what happens when I run into:

```
root@murray:/home/bill# sudo apt-get -f remove wireshark wireshark-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpcap0.8 : Breaks: libpcap0.8:i386 (!= 1.5.3-2) but 1.4.0-2 is to be installed
 libpcap0.8:i386 : Breaks: libpcap0.8 (!= 1.4.0-2) but 1.5.3-2 is to be installed
 libpcap0.8-dev:i386 : Depends: libpcap0.8:i386 (= 1.5.3-2) but 1.4.0-2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Following the instructions gives me this:

```
root@murray:/home/bill# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libstdc++-4.8-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpcap0.8:i386
The following packages will be upgraded:
  libpcap0.8:i386
1 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
3 not fully installed or removed.
Need to get 0 B/108 kB of archives.
After this operation, 9,216 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 216931 files and directories currently installed.)
Preparing to unpack .../libpcap0.8_1.5.3-2_i386.deb ...
Unpacking libpcap0.8:i386 (1.5.3-2) over (1.4.0-2) ...
dpkg: error processing archive /var/cache/apt/archives/libpcap0.8_1.5.3-2_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/man/man7/pcap-filter.7.gz', which is different from other instances of package libpcap0.8:i386
Processing triggers for man-db (2.6.7.1-1) ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And for reference the command I tried to use when rolling back libpcap:

```
wget http://mirrors.kernel.org/ubuntu/pool/main/libp/libpcap/libpcap0.8_1.4.0-2_i386.deb http://mirrors.kernel.org/ubuntu/pool/main/libp/libpcap/libpcap0.8-dev_1.4.0-2_i386.deb
```

then install: ```
sudo dpkg -i libpcap0.8_1.4.0-2_i386.deb libpcap0.8-dev_1.4.0-2_i386.deb Note: if you have a 64bit OS, then change out to: libpcap0.8_1.4.0-2_amd64.deb libpcap0.8-dev_1.4.0-2_amd64.deb

sudo dpkg -i libpcap0.8_1.4.0-2_amd64.deb libpcap0.8-dev_1.4.0-2_amd64.deb
```

I just hopped back on the Ubuntu wagon after 3 years away, and I know the forums are great so thank you very much to anyone who can help me get this sorted out! :p

---

### Post by Jsmooth622 on 2014-09-28
I too am having this exact error, can not upgrade filesystem until this is resolved. PLEASE HELP!!!

---

### Post by ediblestarling on 2014-09-30
I thing it's time for a bit of a bump. Anyone able to help? I was thinking maybe I could just manually delete the files causing the conflict, but I don't know where to look for them.

---

### Post by Bashing-om on 2014-09-30
ediblestarling; Hello;

I can see where this could get "nasty", but as it has been so long and no other has responded; I will see what we can do.
What results:
```

sudo apt-get remove libpcap0.8

``` 
As we are messing about with system libraries, I strongly advise NOT to reboot the system once we start until this situation is under control.

Depending on how that command runs, and what the package manager advises is what determines our next step.

[INDENT]the longest journey begins
[INDENT][INDENT][INDENT]with that 1st step
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ediblestarling on 2014-10-01
Yay! thanks for jumping down the rabbit hole with us. This is what I get:

```
colin@powell:~$ sudo apt-get remove libpcap0.8
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpcap0.8-dev:i386 : Depends: libpcap0.8:i386 (= 1.5.3-2) but 1.4.0-2 is to be installed
 ppp : Depends: libpcap0.8 (>= 0.9.8) but it is not going to be installed
 reaver : Depends: libpcap0.8 (>= 0.9.8) but it is not going to be installed
 tcpdump : Depends: libpcap0.8 (>= 1.2.1) but it is not going to be installed
 wireshark : Depends: libpcap0.8 (>= 0.9.8) but it is not going to be installed
 wireshark-common : Depends: libpcap0.8 (>= 1.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2014-10-01
ediblestarling; Good morning !

A bit the wiser, let's try:
```

sudo apt-get remove libpcap0.8-dev:i386

```
See what that will do for us,
As we work toward removing 'wireshark' .

[INDENT][INDENT]a piece at the time
[/INDENT][/INDENT]

---

### Post by ediblestarling on 2014-10-01
Aye aye cap'n! Here's what I get (spoiler: more of the same):

```
george@michaels:~$ sudo apt-get remove libpcap0.8-dev:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpcap0.8 : Breaks: libpcap0.8:i386 (!= 1.5.3-2) but 1.4.0-2 is to be installed
 libpcap0.8:i386 : Breaks: libpcap0.8 (!= 1.4.0-2) but 1.5.3-2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Bashing-om on 2014-10-01
ediblestarling; Well shucks !

As round and around we go !
Let's see if we can find out why we go R and R.
What returns:
```

apt-cache policy libpcap0.8
apt-cache policy libpcap0.8:i386

```

Presently the package manager says:
- ppp
- reaver
- tcpdump
- wireshark
- wireshark-common
Are broken !

Keeping in mind:
> 
dpkg: error processing archive /var/cache/apt/archives/libpcap0.8_1.5.3-2_i386.deb (--unpack):
 such that there may be another way to deal with this.

Looking for a way
[INDENT][INDENT][INDENT]to break this viscous cycle
[/INDENT][/INDENT][/INDENT]

---

### Post by Jsmooth622 on 2014-10-01
Firstly thank you for taking the time to help us with our dilemma! After imputing the above code, it returns:

thechildren@TheChildren:~$ apt-cache policy libpcap0.8
libpcap0.8:
  Installed: 1.5.3-2
  Candidate: 1.5.3-2
  Version table:
 *** 1.5.3-2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
thechildren@TheChildren:~$ apt-cache policy libpcap0.8:i386
libpcap0.8:i386:
  Installed: 1.4.0-2
  Candidate: 1.5.3-2
  Version table:
     1.5.3-2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
 *** 1.4.0-2 0
        100 /var/lib/dpkg/status
thechildren@TheChildren:~$

---

### Post by Bashing-om on 2014-10-01
Jsmooth622; Well, maybe;

In your case try:
```

sudo apt-get remove libpcap0.8:i386

``` and we see what results, and where to go from here.
Please use code tags for the command outputs, to maintain formatting and readability.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ediblestarling on 2014-10-01
I got something similar, going to format it a bit more:

```
george@foreman:~$ apt-cache policy libpcap0.8
libpcap0.8:
  Installed: 1.5.3-2
  Candidate: 1.5.3-2
  Version table:
 *** 1.5.3-2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

and

```
stephen@night:~$ apt-cache policy libpcap0.8:i386
libpcap0.8:i386:
  Installed: 1.4.0-2
  Candidate: 1.5.3-2
  Version table:
     1.5.3-2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
 *** 1.4.0-2 0
        100 /var/lib/dpkg/status
```

Thanks again for your help!

---

### Post by Bashing-om on 2014-10-01
ediblestarling; Welp;

We done visited 'libpcap0.8:i386'. Presently I see no point  in going back.
But, I do note :
> 
tcpdump : Depends: libpcap0.8 (>= 1.2.1) but it is not going to be installed

Is holding 'libpcap0.8' to that lower version !

Let's try:
```

sudo dpkg -P tcpdump

```

see if that releases the round robin.

[INDENT][INDENT][INDENT]could be
[/INDENT][/INDENT][/INDENT]

---

### Post by ediblestarling on 2014-10-01
Well that ran without a hitch! Next?

```
james@blunt:~$ sudo dpkg -P tcpdump
[sudo] password for james: 
(Reading database ... 216930 files and directories currently installed.)
Removing tcpdump (4.5.1-2ubuntu1) ...
Purging configuration files for tcpdump (4.5.1-2ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
```

---

### Post by Bashing-om on 2014-10-01
ediblestarling; Looks promising !

try now:
```

sudo apt-get remove wireshark

```
and let's see !

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by mc4man on 2014-10-01
did you try removing both i386 packages at the same time, 
```
sudo apt-get purge libpcap0.8-dev:i386 libpcap0.8:i386
```

---

### Post by ediblestarling on 2014-10-01
Hmm...looks familiar :eek:

```
bob@marley:~$ sudo apt-get remove wireshark
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpcap0.8 : Breaks: libpcap0.8:i386 (!= 1.5.3-2) but 1.4.0-2 is to be installed
 libpcap0.8:i386 : Breaks: libpcap0.8 (!= 1.4.0-2) but 1.5.3-2 is to be installed
 libpcap0.8-dev:i386 : Depends: libpcap0.8:i386 (= 1.5.3-2) but 1.4.0-2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by ediblestarling on 2014-10-01
Aha, that seemed to do something useful:

```
bob@marley:~$ sudo apt-get purge libpcap0.8-dev:i386 libpcap0.8:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libc6-dev:i386 libstdc++-4.8-dev linux-libc-dev:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libpcap0.8:i386* libpcap0.8-dev:i386*
0 upgraded, 0 newly installed, 2 to remove and 34 not upgraded.
3 not fully installed or removed.
After this operation, 869 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 216917 files and directories currently installed.)
Removing libpcap0.8-dev (1.5.3-2) ...
Removing libpcap0.8:i386 (1.4.0-2) ...
Purging configuration files for libpcap0.8:i386 (1.4.0-2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Setting up libpcap0.8:amd64 (1.5.3-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...

```

And then I was able to remove wireshark and that dastardly reaver! Now, do I need to reinstall tcpdump? Also, can you explain to this noob why that worked but it wouldn't work when they were separate commands?!

---

### Post by mc4man on 2014-10-02
The short story would be you had mismatched i386 packages for libpcap0.8-dev & libpcap0.8 & the libpcap0.8 one was mismatched to your current amd64 libpcap0.8
(- i386 & amd64 packages need to be same version, -dev & lib packages need to also match

So if you tried to remove libpcap0.8-dev:i386 it still had the issue of libpcap0.8:i386 being  the wrong version for libpcap0.8 (amd64 
If you tried to remove libpcap0.8:i386 then libpcap0.8-dev:i386 was still installed & deped on libpcap0.8:i386  (which was also the wrong version 

In other words a little bit of a mess compounded by installing the -dev & i386 packages.

---

### Post by Jsmooth622 on 2014-10-02
Thank you, apologize for improper format I am new to the forums! Will make sure to use code tags from now on. Code seems to have worked, running "sudo apt-get upgrade" now to see.

---

### Post by Jsmooth622 on 2014-10-02
Everything is back to normal!! Greatly appreciate the help!!!

---

### Post by ediblestarling on 2014-10-02
Nice, that makes sense! Thanks a million to both of you folks for helping out. You can mark this resolved or whatever they need to on here.

---

### Post by Bashing-om on 2014-10-02
ediblestarling; Outstandingly great !

mc4man saves the day !

Only you can say when/if your condition is satisfied by -you- marking the thread solved.
Top of the post -> thread tools.

[INDENT][INDENT]and just keep on keep'n on
[/INDENT][/INDENT]

---

