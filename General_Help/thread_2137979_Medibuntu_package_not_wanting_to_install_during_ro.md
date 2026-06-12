---
title: "Medibuntu package not wanting to install during routine upgrades"
date: 2013-04-22
forum: General Help
---

### Post by send2 on 2013-04-22
Hi all,

when running my update manager during a routine update request, I got the following error from the Medibuntu package:

[ATTACH=CONFIG]241656[/ATTACH][ATTACH=CONFIG]241657[/ATTACH]

there seems to be an error about a key missing but I was not able to get a picture of that. I hope this is sufficient for problem solving. How would I go about solving this or do I need to include additional steps. 

TIA

Edit: after using apt-get update I got the following info from terminal:

```

W: GPG error: http://packages.medibuntu.org precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

---

### Post by oldos2er on 2013-04-22
Add the key with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [COLOR=#000000][FONT=Ubuntu Mono]2EBC26B60C5A2783

sudo apt-get update
```[/FONT][/COLOR]

---

### Post by send2 on 2013-04-22
> **oldos2er said:**
> Add the key with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [COLOR=#000000][FONT=Ubuntu Mono]2EBC26B60C5A2783

sudo apt-get update[/FONT][/COLOR]
```

Thanks to you oldos2er, that did corrected the problem :)

---

