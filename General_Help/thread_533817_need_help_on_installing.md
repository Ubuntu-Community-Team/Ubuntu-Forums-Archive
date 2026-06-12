---
title: "need help on installing"
date: 2007-08-24
forum: General Help
---

### Post by wolfx28 on 2007-08-24
well i've read a little bit into it and i can't seem to install withoout getting an error message so i tried using the terminal to install kdmtheme manager

so i did

sudo apt-get (and aptitude) install kdmtheme

it loads a bunh of stuff then i get this error

Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)

what can i do ?

Wolf

---

### Post by Happy_Man on 2007-08-24
That's odd...... on my Kubuntu feisty install, kdmtheme doesn't have any dependencies that weren't already installed for me, and goes without a hitch. I know I have never worked with any packages like the ones you describe..... that's really weird. In any case, do this:

```
sudo apt-get -f install
```

That forces it to install anything left. Once that finishes, ```
sudo apt-get update && sudo apt-get upgrade
```

Alternate between those two commands until you find the offending dependency package, and then eliminate it.

---

### Post by prince_niceguy on 2007-08-24
Have you tried installing through the synaptic or adept. Do they give the same error. Are you trying to install clvm or any of the software which you have listed? 

And yes it is possible and it is done that a windows guy can use linux ;-)... I am example of the same... :-)...

---

### Post by wolfx28 on 2007-08-24
ok first i did the sudo install -f thing and the update and upgrade and i got this

7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

i have tried synaptic and got this message 

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

Wolf

---

### Post by wolfx28 on 2007-08-24
any ssuggestions?

Wolf

---

### Post by wolfx28 on 2007-08-25
i guess not..:( if i cant install anything then there isint much point of haing linux on my comp

:(

Wolf

---

### Post by Happy_Man on 2007-08-25
I have an idea. Why don't you try again after deleting the contents of /var/cache/apt/archives. That may help a bit.

---

### Post by oldos2er on 2007-08-25
Try [http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html](http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html)

---

