---
title: "Automatix2 Installation Error on Edgy"
date: 2006-11-07
forum: General Help
---

### Post by bg1256 on 2006-11-07
I was attempting to install Automatix2 based on a guide found [here]("http://www.ubuntuforums.org/showthread.php?t=277677&highlight=edgy+automatix").

I added the repo, but when I ran sudo apt-get update, I got the following error:
> W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: You may want to run apt-get update to correct these problems


Not sure what to do... ran a search of the forums, but it seems that this is working for most people, and it should be working for me.\

edit: nvm I followed the instructions[here,]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_with_Apt")and all is well.

---

### Post by taurus on 2006-11-07
From a terminal, Applications -> Accessories -> Terminal, type

```

wget http://www.getautomatix.com/apt/key.gpg.asc
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -

```
[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)

---

### Post by strabes on 2006-11-07
usually it's best to follow guides from a developer's own website, in this case, [www.getautomatix.com](www.getautomatix.com). Forum howtos seem to be frequently outdated.

---

