---
title: "Uninstall This Line?"
date: 2012-12-16
forum: General Help
---

### Post by ProxyCyber on 2012-12-16
In terminal, how do I uninstall 

sudo add-apt-repository ppa:upubuntu-com/tor

How do I uninstall that whole line in terminal? 

Also, can someone please tell me how to make Tor work?! All the times I've tried installing and making tor work, it says 

Vidalia detected that the Tor software exited unexpectedly. Please check the message log for recent warning or?

BUT FIRST, please tell me how to UNINSTALL IN TERMINAL, the line sudo add-apt-repository ppa:upubuntu-com/tor

---

### Post by Bucky Ball on 2012-12-16
Welcome to the forums. You don't need to do in terminal. Open Update Manager then hit 'Settings' in the bottom left corner. Click the 'Other Software' tab and just untick the offending repo.

In a terminal, you could edit the sources.list file and put a hash (#) in front of the offending repo:

```
sudo nano /etc/apt/sources.list
```

Or remove the repo line(s) completely. Might be best to do a backup of that file before tweaking in case you screw up, with:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

... and if you screw up:

```
sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list
```

---

### Post by ProxyCyber on 2012-12-16
> **Bucky Ball said:**
> Welcome to the forums. You don't need to do in terminal. Open Update Manager then hit 'Settings' in the bottom left corner. Click the 'Other Software' tab and just untick the offending repo.

In a terminal, you could edit the sources.list file and put a hash (#) in front of the offending repo:

```
sudo nano /etc/apt/sources.list
```

Or remove the repo line(s) completely. Might be best to do a backup of that file before tweaking in case you screw up, with:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

... and if you screw up:

```
sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list
```

Thanks. But now, when I do sudo apt-get update, it says 

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by steeldriver on 2012-12-16
> **ProxyCyber said:**
> E: Unable to lock the administration directory (/var/lib/dpkg/), **is another process using it?**

do you have Software Center or Synaptic open? if so close it then try again

---

### Post by ProxyCyber on 2012-12-16
> **steeldriver said:**
> do you have Software Center or Synaptic open? if so close it then try again

Alright, now it's good, BUT it now says 

Reading package lists... Done
W: GPG error: [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F24AEA9FB05498B7

---

### Post by Bucky Ball on 2012-12-16
Either the steampowered repo is out of action or it has not been added correctly (you also need to add the key).

You can also disable this repo and try again or go back over the installation steps and see if you have forgotten to obtain the key ...

---

### Post by ProxyCyber on 2012-12-16
> **Bucky Ball said:**
> Either the steampowered repo is out of action or it has not been added correctly (you also need to add the key).

You can also disable this repo and try again or go back over the installation steps and see if you have forgotten to obtain the key ...

You rock. Removed Steampowered. Thank you.

---

### Post by oldos2er on 2012-12-17
> **ProxyCyber said:**
> In terminal, how do I uninstall 

sudo add-apt-repository ppa:upubuntu-com/tor

How do I uninstall that whole line in terminal? 


Just FYI since I see your problem is already solved, ```
sudo add-apt-repository -r ppa:upubuntu-com/tor
```

---

### Post by Bucky Ball on 2012-12-18
Glad to help. Please mark thread as 'Solved' from Thread Tools to help others. ;)

---

