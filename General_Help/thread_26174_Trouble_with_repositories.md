---
title: "Trouble with repositories ?"
date: 2005-04-12
forum: General Help
---

### Post by rbarth on 2005-04-12
I'm trying to get the file "libqt3c102" but I am having some problems, below are some of the messages that I recieve.

After running "apt-get update" these are the messages that I recieve.

> W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures could n't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B 907

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures cou ldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F4 1B907

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures coul dn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41 B907

The program then recomends:

> W: You may want to run apt-get update to correct these problems


I do this again but get the same result.
I've checked some of the posts, and found this method

 > # sudo apt-get install libqt3c102 libqt3c102-mt libqt3c102-ibase

And it stops with the first file, with the following message.

> Package libqt3c102 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqt3c102 has no installation candidate

Then I tried

 > # apt-get install libqt3c102-mt libqt3c102-ibase

These are the messages that I recieve.

> Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqt3c102-mt has no installation candidate

And so on, does anyone have any ideas on how to make this work.

Thank You,

Bob

---

### Post by erkki70 on 2005-04-12
Hi,
Someone correct me if I'm wrong but libqt3c102 is meant to be in the Universe repository, isn't it?
So I guess you need to enable the Universe repos. in your sources.list to install the libs.

Hope this helps.

Cheers,
Erkki.

---

### Post by lao_V on 2005-04-12
>  			 				W: GPG error: [ftp://ftp.nerim.net]("ftp://ftp.nerim.net/") stable Release: The following signatures could n't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B 907

W: GPG error: [ftp://ftp.nerim.net]("ftp://ftp.nerim.net/") unstable Release: The following signatures cou ldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F4 1B907

W: GPG error: [ftp://ftp.nerim.net]("ftp://ftp.nerim.net/") testing Release: The following signatures coul dn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41 B907 

This would suggest that you haven't set up your key for the nerim repositories. Have you carried out the following steps?

 ```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update
``` 

as described in [http://www.ubuntuguide.org]("http://www.ubuntuguide.org")

---

### Post by rbarth on 2005-04-12
Thank You.... Loa_V, redid the key and all works well now.

Bob

---

