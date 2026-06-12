---
title: "installing TOR on Ubuntu 17.10"
date: 2017-12-03
forum: General Help
---

### Post by hunterkasy on 2017-12-03
I am trying to install TOR on Ubuntu because I want to run a relay, I have done this before with no problems.  here is what I have done:

You need to add the following entry in /etc/apt/sources.list or a new file in /etc/apt/sources.list.d/:
```
    deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) xenial main
    deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) xenial main
```
Then add the gpg key used to sign the packages by running the following commands at your command prompt:
```
    gpg --keyserver keys.gnupg.net --recv A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89
    gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```
You can install it with the following commands:
```
    $ apt update
    $ apt install tor deb.torproject.org-keyring
```
after I do the last command I get this:
```
tyler@tyler-quad-17:~$ sudo apt install tor deb.torproject.org-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 tor : Depends: libevent-2.0-5 (>= 2.0.10-stable) but it is not installable
       Recommends: tor-geoipdb but it is not going to be installed
       Recommends: torsocks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
tyler@tyler-quad-17:~$
```

---

### Post by photonxp on 2017-12-04
Why choose to use **xenial** instead of **stretch**?
> 
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) **stretch** main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) **stretch** main

---

### Post by hunterkasy on 2017-12-04
> **photonxp said:**
> Why choose to use **xenial** instead of **stretch**?

I get the same error

---

### Post by arav.prasad on 2018-01-01
The " Xenial " use is for ubuntu 16.04 and "Stretch" is for debian as seen in the website of torprojects [https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)
I guess they have not launched a new version for "Aadvark" which is 17.10

---

### Post by oceansailor on 2018-11-03
Just had the same problem. You have to fix it manually. Download the package here: [https://packages.debian.org/stretch/amd64/libevent-2.0-5/download](https://packages.debian.org/stretch/amd64/libevent-2.0-5/download)  

And then install it manually with: [B]
sudo apt install ./libevent-2.0-5_2.0.21-stable-3_amd64.deb[/B]

---

### Post by coffeecat on 2018-11-03
Back to sleep old thread.

Closed.

---

