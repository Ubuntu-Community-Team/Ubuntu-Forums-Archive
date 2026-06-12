---
title: "Problem with dependencies"
date: 2007-05-28
forum: General Help
---

### Post by misfito on 2007-05-28
Hello i got this message and don't know what to do:

> 
E: Problem parsing dependency Depends
E: Error occurred while processing thekompany-support (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_edgy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)


and also:

> 
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3

---

### Post by MoLE on 2007-06-05
This seems to be an automatix problem, as apt is complaining it can't access the getautomatix.com repository.

I would suggest running through the [automatix2 installation]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.10_i386.2CAMD64_.28Edgy.29") again, as this process will ensure you have the correct GPG keys installed and will refresh the repository for you.

If that doesn't work, then I'd suggest the automatix2 forums - they are quite happy to support their own product there.

---

