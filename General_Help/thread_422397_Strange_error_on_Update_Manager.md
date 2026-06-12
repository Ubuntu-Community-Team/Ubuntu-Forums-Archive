---
title: "Strange error on Update Manager"
date: 2007-04-25
forum: General Help
---

### Post by stuart_75 on 2007-04-25
I get this error when running update manager, and I now have to use Synaptic for any updates.....

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3

Any clues on how to fix it?????

Thanks!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by zvacet on 2007-04-25
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -
[/B]
and in your case

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
 gpg --export --armor 58403026387EE263  | sudo apt-key add -

do the same with second one

---

### Post by stuart_75 on 2007-04-25
Thanks, seems to of got rid of the error messages.

Now Im looking to upgrage to the latest version of Ubuntu, but I dont get the upgrade icon when I run Update manager. Other than downloading the iso image is there any way to get the upgrade option icon?

---

### Post by zvacet on 2007-04-25
```
sudo aptitude update
```

Your system must be up-to-date to show distro upgrade in update manager.I still think that iso is better choice.I prefer alternate CD,bacause I can upgrade from disc and if anything goes wrong I have Cd to reinstall.But,that´s just me.

---

### Post by stuart_75 on 2007-04-25
Thanks for that, it seems my update manager is stuck at version 0.42.2. Ive tried to update it to 0.45.2 with no luck. Anyway of forcing the update??

Cheers!!!!

---

### Post by emiliorecio on 2007-05-04
Hi. I have the same problem. Googlenadola, i found this explanation:
In Argentina Telefonica provide Internet service as Speedy. The proxy servers of speedy don't renew the cache from some days.  So i do this:
1 - Create this script:
$$> sudo gedit script.sh

#!/bin/bash
export http_proxy=http://$1
apt-get update

2 - $$> chmod 755 script.sh

3 - run

$$> ./script.sh IP

were ip is one from this page [http://www.echolink.org/proxylist.asp](http://www.echolink.org/proxylist.asp)
This IP's are anonymous proxy servers. Use google to find more.

4 - run apt=get

$$> sudo apt-get update
If work go to step 5 
else go step 3
I need to probe this 3 times because some proxys don't work.

5 - Disable variable proxy
$$> export http_proxy= 

6- run apt-get upgrade

It's work for me. I hope this work for you

Saludos!

---

### Post by zvacet on 2007-05-04
[https://wiki.ubuntu.com/EdgyUpdatesEnabled]("https://wiki.ubuntu.com/EdgyUpdatesEnabled")

---

