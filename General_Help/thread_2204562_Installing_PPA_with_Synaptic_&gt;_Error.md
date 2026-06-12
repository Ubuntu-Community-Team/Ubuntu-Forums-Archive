---
title: "Installing PPA with Synaptic &gt; Error"
date: 2014-02-09
forum: General Help
---

### Post by 2CV67 on 2014-02-09
I have been using Synaptic for many years but recently (since 13.10??) I am starting to get error messages like the following when I "reload" Synaptic after adding a PPA:
```
W: GPG error: http://ppa.launchpad.net saucy Release: 
The following signatures couldn't be verified because the public key is not available: 
NO_PUBKEY A8AA1FAA3F055C03
```
The PPAs function OK after I accept the warning.

I tracked this down to needing to Import a Key File in Synapt > Settings > Repositories >  Authentication tab.

I did find a laborious way of importing a key:
From the PPA page > Technical details > Signing key > Web page > Copy key > paste to text file > "Import Key File" > Navigate to text file.

I don't remember having to do that previously.

Has something changed?

Is there an easier way of handling these key files USING SYNAPTIC?

PLEASE don't point me to (however simple) ways of doing it by Command Line.
I am aware of those, but want to stick with GUI...

Thanks!

---

### Post by Dave_L on 2014-02-09
I normally prefer to use synaptic for installing and updating packages.  But I've found that the add-apt-repository command takes care of the key issue automatically, with no additional steps required.

I haven't found a way of doing the equivalent of add-apt-repository solely from synaptic.

---

