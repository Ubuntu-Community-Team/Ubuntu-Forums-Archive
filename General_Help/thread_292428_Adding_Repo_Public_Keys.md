---
title: "Adding Repo Public Keys"
date: 2006-11-03
forum: General Help
---

### Post by musther on 2006-11-03
I just added a few repos to my sources.list, and now at the end of an apt-get update I get:

```
W: GPG error: http://packages.freecontrib.org edgy-plf Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: GPG error: http://www.elisanet.fi edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: You may want to run apt-get update to correct these problems
```

I've forgotten how to add the keys, can someone tell me please.

---

### Post by bettlebrox on 2006-11-03
sudo apt-get add keyfile

---

### Post by mmcmonster on 2006-11-03
> **musther said:**
> I just added a few repos to my sources.list, and now at the end of an apt-get update I get:

```
W: GPG error: http://packages.freecontrib.org edgy-plf Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: GPG error: http://www.elisanet.fi edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: You may want to run apt-get update to correct these problems
```I've forgotten how to add the keys, can someone tell me please.

Hint (which you wont forget :-) ) - 
Google for D0AFFF5E937215FF
(or whatever the key you are looking for)
For the lazy: [D0AFFF5E937215FF]("http://ubuntuforums.org/showpost.php?p=1238861&postcount=21") and [F120156012B83718]("http://ubuntuforums.org/showpost.php?p=1600411&postcount=2").

---

### Post by AceRimmer on 2006-11-10
> **bettlebrox said:**
> sudo apt-get add keyfile

I am getting this error 
> 
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C

but when I try your method I get an error:

> E: Invalid operation add

---

### Post by bettlebrox on 2006-11-11
> **AceRimmer said:**
> I am getting this error 

but when I try your method I get an error:

Did U download the key and add it?

---

### Post by n3Cre0 on 2006-11-18
Just peeping in here to give the solution.

First "wget <urlwithkeyfile>"
Then "sudo apt-key add <keyjustdownloaded>"
And to finish "rm <keyjustdownloaded>"

---

