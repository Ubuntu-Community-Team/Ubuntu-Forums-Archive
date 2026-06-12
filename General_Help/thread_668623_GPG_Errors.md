---
title: "GPG Errors"
date: 2008-01-15
forum: General Help
---

### Post by sgtbob on 2008-01-15
How do I get the following errors corrected?  What do I do?

W: GPG error: [http://lug.mtu.edu](http://lug.mtu.edu) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://lug.mtu.edu](http://lug.mtu.edu) gutsy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://lug.mtu.edu](http://lug.mtu.edu) gutsy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://lug.mtu.edu](http://lug.mtu.edu) gutsy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://lug.mtu.edu](http://lug.mtu.edu) gutsy-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263


Bob :confused:

---

### Post by bodhi.zazen on 2008-01-15
Try this :

```
gpg –-recv-keys 40976EAF437D05B5
gpg –-export –armor 40976EAF437D05B5 | sudo apt-key add -
```

---

### Post by sgtbob on 2008-01-16
You are talking to a real dummy here. 

Do you mean that these instructions need to be entered into a terminal?  I was able to run the first one, with the following result:

[B]bob@XPS:~$ gpg –-recv-keys 40976EAF437D05B5
gpg: directory `/home/bob/.gnupg' created
gpg: new configuration file `/home/bob/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/bob/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/bob/.gnupg/secring.gpg' created
gpg: keyring `/home/bob/.gnupg/pubring.gpg' created
usage: gpg [options] [filename][/B]

Not knowing what I had achieved, I ran the second one which stalled but returned the following:
[B]
bob@XPS:~$ gpg –-export –armor 40976EAF437D05B5 | sudo apt-key add -
[sudo] password for bob:usage: gpg [options] [filename][/B]

Since the system hung at this point, I am unsure what I have accomplished.

Bob

---

### Post by sgtbob on 2008-01-16
I note that the 'dashes' preceding the 'recv' entry appear to be different.  Are these truly dashes?

---

### Post by sgtbob on 2008-01-16
Well - after trying several variations of your suggestions, I was able to 'reload' my files and did not get the gpg error.  

I did note that I had to substitute another number to acquire the data as you suggested. Evidently the 'gpg' errors can involve more than one number, so by entering the other numbers, I was able to do as you suggested.

Many thanks for hte advice and for causing me to think about how this could be resolved.

Bob

---

### Post by kevdog on 2008-01-16
The original command should have been

gpg –-export –-armor 40976EAF437D05B5 | sudo apt-key add -

Also if you do a:

gpg --list-keys

The number of the above key should be listed in the second column.  You could use this number as the key identity and add it to the apt keyring this way also

---

### Post by rustutzman on 2008-01-17
The easiest way I've found to fix key errors is to use the APT Key Manager to add the keys. It's available through the Synaptic Package Manager.

---

