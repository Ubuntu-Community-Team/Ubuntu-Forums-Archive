---
title: "Problem with APT-UPGRADE"
date: 2018-01-19
forum: General Help
---

### Post by giulianosigma on 2018-01-19
Hey there.

I've been running **sudo apt-get upgrade** and I'm getting the following errors:

```

W: The repository 'http://sft.if.usp.br/ubuntu zesty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://sft.if.usp.br/ubuntu zesty-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://sft.if.usp.br/ubuntu zesty-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/mc3man/xerus-media/ubuntu zesty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://download.fpcomplete.com/ubuntu xenial Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 575159689BEFB442
W: The repository 'http://download.fpcomplete.com/ubuntu xenial Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://sft.if.usp.br/ubuntu/dists/zesty/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://sft.if.usp.br/ubuntu/dists/zesty-updates/main/binary-i386/Packages  404  Not Found
E: Failed to fetch http://sft.if.usp.br/ubuntu/dists/zesty-security/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/mc3man/xerus-media/ubuntu/dists/zesty/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.



```

Any ideias how to solve this? I've tried many solutions I found googling around, but none of them made any changes to the output.

Thanks!

---

### Post by Bashing-om on 2018-01-19
giulianosigma; Ouch -

You are now late to the party - zesty has reached End_Of_Life and the repository no longer exist.
[http://fridge.ubuntu.com/2018/01/17/ubuntu-17-04-zesty-zapus-reached-end-of-life-on-january-13-2018/](http://fridge.ubuntu.com/2018/01/17/ubuntu-17-04-zesty-zapus-reached-end-of-life-on-january-13-2018/)

Upgrade to 17.10 :
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Or a clean fresh install .

[INDENT][INDENT]nothing last forever
[/INDENT][/INDENT]

---

### Post by giulianosigma on 2018-01-22
Thanks alot!

Will upgrade.

---

