---
title: "I need some help installing Tor"
date: 2012-12-07
forum: General Help
---

### Post by andreamillspaugh on 2012-12-07
Hi, everyone, I wont to install Tor and this is what I followed .
```
        **[Option one: Tor on Debian squeeze, Debian sid, or Debian testing]("https://www.torproject.org/docs/debian.html.en#debian")**

 
 If you're using Debian, just run
apt-get install tor as root. 
  Note that this might not always give you the latest stable Tor version, but you will receive important security fixes. To make sure that you're running the latest stable version of Tor, see option two below. 
  Now Tor is installed and running. Move on to [step two]("https://www.torproject.org/docs/tor-doc-unix.html.en#using") of the "Tor on Linux/Unix" instructions. 
    **[Option two: Tor on Ubuntu or Debian]("https://www.torproject.org/docs/debian.html.en#ubuntu")**

 
 **Do not use the packages in Ubuntu's universe.** In the past they have not reliably been updated. That means you could be missing stability and security fixes. 
  You'll need to set up our package repository before you can fetch Tor. First, you need to figure out the name of your distribution. A quick command to run is lsb_release -c or cat /etc/debian_version. Here's a quick mapping: 

[LIST]
[*] Debian unstable (sid) is "sid"
[*] Debian testing is "wheezy"
[*] Debian 6.0 (squeeze) is "squeeze"
[*] Debian 5.0 (lenny) is "lenny"
[*] Ubuntu 12.04 is "precise"
[*] Ubuntu 11.10 is "oneiric"
[*] Ubuntu 11.04 is "natty"
[*] Ubuntu 10.10 or Trisquel 4.5 is "maverick"
[*] Ubuntu 10.04 or Trisquel 4.0 is "lucid"
[*] Ubuntu 9.10 or Trisquel 3.5 is "karmic"
[*] Ubuntu 8.04 is "hardy"
[/LIST]
 Then add this line to your /etc/apt/sources.list file:
deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main  where you put the codename of your distribution (i.e. lenny, sid, maverick or whatever it is) in place of <DISTRIBUTION>.   Then add the gpg key used to sign the packages by running the following commands at your command prompt: 
gpg --keyserver keys.gnupg.net --recv 886DDD89 gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -  Now refresh your sources, running the following command (as root) at your command prompt: apt-get update  If there are no errors you're good to continue.   We provide a Debian package to help you keep our signing key current. It is recommended you use it. Install it using 
apt-get install deb.torproject.org-keyring    To finally install Tor just run: 
apt-get install tor    Now Tor is installed and running. Move on to [step two]("https://www.torproject.org/docs/tor-doc-unix.html.en#using") of the "Tor on Linux/Unix" instructions. 
  The DNS name deb.torproject.org is actually a set of independent servers in a DNS round robin configuration. If you for some reason cannot access it you might try to use the name of one of its part instead. Try deb-master.torproject.org, mirror.netcologne.de or tor.mirror.youam.de. 
   **[Option three: Using the development branch of Tor on Debian or Ubuntu]("https://www.torproject.org/docs/debian.html.en#development")**

 
If you want to use the [development branch]("https://www.torproject.org/download/download.html.en#packagediff") of Tor instead (more features and more bugs), you need to add a different set of lines to your /etc/apt/sources.list file:

deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) experimental-<DISTRIBUTION> main  where you again substitute the name of your distro (lenny, sid, maverick, ...) in place of <DISTRIBUTION>.   Then run the following commands at your command prompt: 
gpg --keyserver keys.gnupg.net --recv 886DDD89 gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - apt-get update apt-get install tor deb.torproject.org-keyring    Now Tor is installed and running. Move on to [step two]("https://www.torproject.org/docs/tor-doc-unix.html.en#using") of the "Tor on Linux/Unix" instructions. 
   **[Building from source]("https://www.torproject.org/docs/debian.html.en#source")**

 
 If you want to build your own debs from source you must first add an appropriate deb-src line to sources.list. 
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main  deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) experimental-<DISTRIBUTION> main  You also need to install the necessary packages to build your own debs and the packages needed to build Tor: apt-get install build-essential fakeroot devscripts apt-get build-dep tor  Then you can build Tor in ~/debian-packages: mkdir ~/debian-packages; cd ~/debian-packages apt-get source tor cd tor-* debuild -rfakeroot -uc -us cd ..  Now you can install the new package: sudo dpkg -i tor_*.deb    Now Tor is installed and running. Move on to [step two]("https://www.torproject.org/docs/tor-doc-unix.html.en#using") of the "Tor on Linux/Unix" instructions. 


```
it dose not work.

---

### Post by snowpine on 2012-12-07
Can you copy & paste the exact terminal output so we can see the error message and hopefully assist you?

---

### Post by andreamillspaugh on 2012-12-07
ok , what am i doing wrong

```
andrea@millspaughdixon:~$ lsb_release -c or cat /etc/debian_version
Usage: lsb_release [options]

lsb_release: error: No arguments are permitted
andrea@millspaughdixon:~$ deb     http://deb.torproject.org/torproject.org
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
andrea@millspaughdixon:~$ clear

andrea@millspaughdixon:~$ apt-get install tor as root
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
andrea@millspaughdixon:~$ sudo -s
[sudo] password for andrea: 
root@millspaughdixon:~# apt-get install tor as root
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package as
E: Unable to locate package root
root@millspaughdixon:~# lsb_release -c or cat /etc/debian_version
Usage: lsb_release [options]

lsb_release: error: No arguments are permitted
root@millspaughdixon:~# lsb_release
No LSB modules are available.
root@millspaughdixon:~# lsb_release -c or cat
Usage: lsb_release [options]

lsb_release: error: No arguments are permitted
root@millspaughdixon:~# $ cat /etc/*-release
$: command not found
root@millspaughdixon:~# DISTRIB_ID=Ubuntu
root@millspaughdixon:~# $ lsb_release -a
$: command not found
root@millspaughdixon:~# DISTRIB_ID=Ubuntu
root@millspaughdixon:~# DISTRIB_RELEASE=7.10
root@millspaughdixon:~# DISTRIB_CODENAME=gutsy
root@millspaughdixon:~# DISTRIB_DESCRIPTION="Ubuntu 7.10"
root@millspaughdixon:~# $ cat /etc/*-release
$: command not found
root@millspaughdixon:~# $ cat /proc/version
$: command not found
root@millspaughdixon:~# cher
No command 'cher' found, did you mean:
 Command 'chef' from package 'filters' (universe)
 Command 'chem' from package 'groff' (main)
 Command 'cver' from package 'gplcver' (universe)
cher: command not found
root@millspaughdixon:~# clear

root@millspaughdixon:~# synclient TouchPadOff=1
root@millspaughdixon:~#  "compizconfig-settings-manager" - also install "compiz" 
compizconfig-settings-manager: command not found
root@millspaughdixon:~# sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
compiz is already the newest version.
compiz-plugins is already the newest version.
compiz-plugins set to manually installed.
The following package was automatically installed and is no longer required:
  librhythmbox-core5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-plugins-extra
The following NEW packages will be installed:
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins-extra
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,653 kB of archives.
After this operation, 6,749 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/universe compiz-plugins-extra i386 0.9.7.0~bzr9-0ubuntu6 [2,648 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/universe compiz-fusion-plugins-extra all 0.9.7.0~bzr9-0ubuntu6 [3,120 B]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main compiz-fusion-plugins-main all 1:0.9.7.0~bzr19-0ubuntu10 [1,356 B]
Fetched 2,653 kB in 6s (402 kB/s)                                              
Selecting previously unselected package compiz-plugins-extra.
(Reading database ... 269874 files and directories currently installed.)
Unpacking compiz-plugins-extra (from .../compiz-plugins-extra_0.9.7.0~bzr9-0ubuntu6_i386.deb) ...
Selecting previously unselected package compiz-fusion-plugins-extra.
Unpacking compiz-fusion-plugins-extra (from .../compiz-fusion-plugins-extra_0.9.7.0~bzr9-0ubuntu6_all.deb) ...
Selecting previously unselected package compiz-fusion-plugins-main.
Unpacking compiz-fusion-plugins-main (from .../compiz-fusion-plugins-main_1%3a0.9.7.0~bzr19-0ubuntu10_all.deb) ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0 ...
Setting up compiz-plugins-extra (0.9.7.0~bzr9-0ubuntu6) ...
Setting up compiz-fusion-plugins-extra (0.9.7.0~bzr9-0ubuntu6) ...
Setting up compiz-fusion-plugins-main (1:0.9.7.0~bzr19-0ubuntu10) ...
root@millspaughdixon:~# 

```

---

### Post by snowpine on 2012-12-07
Based on your current level of Linux knowledge, I recommend that you steer clear of the terminal and install Tor with a couple of mouse clicks in the Software Center as described here:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Frogs Hair on 2012-12-07
I am not a tor user but have installed the browser bundle from the link successfully just to experiment with it it .[https://www.torproject.org/download/download](https://www.torproject.org/download/download)

---

### Post by andreamillspaugh on 2012-12-07
Im Sorry I just started to learning linux and I like this operating system better then windows, so im just learning as I go thanks for your time.

---

### Post by andreamillspaugh on 2012-12-07
I have one more thing to ask, sorry. what is the command to make the hard drive be able to put files there because it just says skip, it wont let me put files in, I want to unlock it where can i fined this command. thanks

---

### Post by vasa1 on 2012-12-07
> **snowpine said:**
> Based on your current level of Linux knowledge, I recommend that you steer clear of the terminal and install Tor ...
+1 but I would go one step further and suggest that until you get more familiar with things including the terminal, avoid Tor.

---

### Post by jim_deadlock on 2012-12-07
Why are you even trying to install it? All you need to do is download the Tor browser bundle and run it, no need to install, it runs out of the box.

---

### Post by andreamillspaugh on 2012-12-07
Im a computer programmer and I heard about the deep web, and I want to do some research on it and when I install it from the Ubuntu software program it installs it but the browser wont open so I cant get to the deep web.:D Ok i got everything working the way i want for now anywas:grin:

---

### Post by jim_deadlock on 2012-12-07
It's mostly drug/weapons dealers and kiddie porn, you'll soon get bored of it.

---

### Post by vasa1 on 2012-12-07
What is the relevance of Tor for accessing the "deep web"?

---

### Post by jim_deadlock on 2012-12-07
These are "onion" websites, they can only be accessed via the Tor network so the owners can't be traced.

---

### Post by vasa1 on 2012-12-07
> **jim_deadlock said:**
> These are "onion" websites, they can only be accessed via the Tor network so the owners can't be traced.
Thanks for your reply. I came across some more here: [Tor and the Deepnet: What price does society pay for anonymity?]("http://nakedsecurity.sophos.com/2012/12/06/tor-deepnet-anonymity/")
Unpleasant stuff.

---

