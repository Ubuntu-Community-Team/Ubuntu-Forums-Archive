---
title: "Allow external commands inside of chroot jail"
date: 2022-06-19
forum: General Help
---

### Post by Drenriza on 2022-06-19
Hi All

Hi have configured SSH key login with

```
ForceCommand internal-sftp
ChrootDirectory /home/jails/home
```

to define a chroot that i dont want my user to leave on their own.

I have configured /home/jails/bin, dev, lib, lib64, etc.

And allowed outside directories through

```
mount --bind
```

Into the jailed user home directory.

The user that i test with can login, and cant leave the jail,
so without knowing for sure since **_this is the first time i play around with this_**, i believe the jail is working as intended.

My question is as follows: I would like to make my jailed user able to execute the commands
$ npm
$ nvm
$ compose

Is that even possible, and what would be a good way to achieve my jailed user being able to execute the above commands?

The commands are used to manage project dependencies that they are to  create within the jail or allowed paths through mount --bind.

I hope that you can provide me with feedback that can allowed me to achieve above or put me in the right direction.

Thanks in advance
Best regards.

---

