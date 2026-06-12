---
title: "Update error in Ubuntu 16.04"
date: 2017-02-16
forum: General Help
---

### Post by notso23 on 2017-02-16
Hi,
  I have been getting the following error everytime I update my computer. I am fairly new to Ubuntu, and love it, but I am not sure what it all means. I do the sudo update as I was told early on that it was the best way to do it and do the auto remove when needed. Everything seems to be going real good so I am not too worried but I would like it perfect :P if possible.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

and I get this error at the end of "sudo apt-get update"

> Reading package lists... Done
W: GPG error: [http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04](http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A7D1D38BEB6D886
W: The repository 'http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04  Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Thank you in advance :cool:

---

### Post by Perfect Storm on 2017-02-16
If you don't need opensuse.org in the repository it may be fault, simply comment it out of your sourcelist.

---

### Post by notso23 on 2017-02-16
Thank you for your quick reply, but I have no idea what it is that you said, I don't understand one little bit. sorry.

---

### Post by Perfect Storm on 2017-02-16
find 'software & Updates'. then in 'Other Software' tab you'll find 'http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04'. Unselect it.

[img]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=Software+Sources.png[/img]

---

### Post by notso23 on 2017-02-16
Oh thank you so much ... it was so simple I feel stupid ... LOL

---

