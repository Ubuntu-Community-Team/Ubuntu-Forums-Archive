---
title: "Better way to update via CLI with apt"
date: 2017-04-06
forum: General Help
---

### Post by Cavsfan on 2017-04-06
For those of us that prefer to update via CLI and not via unattended-upgrades in the background.

First that has to be done if you want to upgrade with just CLI.

There are two ways to disable unattended-upgrades:
One from 1fallen: [https://ubuntuforums.org/showthread.php?t=2356536&p=13625050#post13625050](https://ubuntuforums.org/showthread.php?t=2356536&p=13625050#post13625050)
And a nuclear option which I chose myself from howefield: [https://ubuntuforums.org/showthread.php?t=2356536&page=2&p=13625357#post13625357](https://ubuntuforums.org/showthread.php?t=2356536&page=2&p=13625357#post13625357)

When we had apt-get I had, as I'm sure many people did an alias in ~/.bashrc file in like this:

```
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean'
```

But, with apt this seems to be a better idea. It produces a nice list you can see which new versions are replacing what older version:

```
alias ud='sudo apt update && apt list --upgradable'
```
Then if there are updates and after you view them this:
```
alias upd='sudo apt upgrade && sudo apt autoclean'
```

Just thought I'd mention it.

---

### Post by Cavsfan on 2017-04-07
Life lesson #2797166391716: never post a new thread without adequate time to be sure it is correct.

I posted some huge errors in the 1st post which have been corrected.

---

