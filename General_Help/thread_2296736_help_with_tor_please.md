---
title: "help with tor please"
date: 2015-09-28
forum: General Help
---

### Post by noob5 on 2015-09-28
Hi,
I just joined the forum yesterday as I knew I would hit a brick wall trying to work out how to use Ubuntu and will be hoping you guys will be able to give me a step by step guide through getting myself set up with different downloads etc.

Todays problem is getting Tor installed.

I have read different ways to install but everything I do fails,so I am hoping you may be able to run me through the process pls.

I am new with computers never mind Ubuntu but i have started here an plan on staying here.

I have tried and failed to install tor and a few other things to no avail and I have reinstalled Ubuntu to start from scratch agiain and this is as far as I am prepared to go untill I get proper advice.

```
noob@noob-HP-Compaq-6910p-RH244AV:~$  sudo add-apt-repository ppa:webupd8team/tor-browser
[sudo] password for noob: 
 Tor Browser Bundle: Anonymous browsing using Firefox and Tor.

More info / feedback: [http://www.webupd8.org/2013/12/tor-browser-bundle-ubuntu-ppa.html](http://www.webupd8.org/2013/12/tor-browser-bundle-ubuntu-ppa.html)

 The Tor software protects you by bouncing your communications
 around a distributed network of relays run by volunteers all
 around the world: it prevents somebody watching your Internet
 connection from learning what sites you visit, it prevents the
 sites you visit from learning your physical location, and it
 lets you access sites which are blocked.

 The Tor Browser Bundle lets you use Tor without needing to
 install any additional software. It comes with a pre-configured
 web browser to protect your anonymity, and is self-contained.
 More info: [https://launchpad.net/~webupd8team/+archive/ubuntu/tor-browser](https://launchpad.net/~webupd8team/+archive/ubuntu/tor-browser)
Press [ENTER] to continue or ctrl-c to cancel adding it
sudo apt-get update
gpg: keyring `/tmp/tmpxscwjq6d/secring.gpg' created
gpg: keyring `/tmp/tmpxscwjq6d/pubring.gpg' created
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpxscwjq6d/trustdb.gpg: trustdb created
gpg: key EEA14886: public key "Launchpad VLC" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
noob@noob-HP-Compaq-6910p-RH244AV:~$ sudo apt-get install tor-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tor-browser
noob@noob-HP-Compaq-6910p-RH244AV:~$
```

If you could break it down were I have to go next as I have read and tried a few different ways to get Tor installed from what people have been saying but as i said I aint getting anywhere fast.

Thx in advance

noob

):P

---

### Post by matt_symes on 2015-09-28
Hi

Did you run

```
sudo apt-get update
```

Before trying to install the tor browser ?

Kind regards

---

### Post by slickymaster on 2015-09-28
*Moved to the ***General Help*** sub-forum*

---

### Post by noob5 on 2015-09-28
I believe I have cracked it,by accident though,any how I am sorted now,
I am sure I will have a new Q shortly regarding something different.
Thx all the same.
noob

---

