---
title: "Trying to keep Vim 8.1 on my machine which was installed from source"
date: 2019-07-27
forum: General Help
---

### Post by frrobert on 2019-07-27
I am running Ubuntu 16.04

I downloaded Vim 8.1 source from the Vim website.  I compiled and installed it.  No problems.  I even created a deb with checkinstall so I could install in on another machine.

Vim 8.1 installs itself in /usr/local/bin and Vim 7.4 installs in /usr/bin so no conflict I thought.  Well Vim 8.1 keeps disappearing off my machine.  I can reinstall it with  but it falls off again.  When I install via deb I get a message I am downgrading Vim.

I even uninstalled Vim 7.4 and the issue continues to happen.  

Someone suggested I am getting the error because the Ubuntu 16.04 has an epoch number and my compiled version does not.  It was suggested I recompile the deb with an epoch number.
I can see where I can enter a version number and revision number but no epoch number.  That was just a suggested solution.  All I really want to do is to keep from having to install Vim 8.1 over and over.

Thanks

---

### Post by #&amp;thj^% on 2019-07-27
It is better to have a install and update source to avoid what your now seeing, that said you could just add a PPA for that.
```
sudo add-apt-repository ppa:jonathonf/vim
```
And;
```

sudo apt update && sudo apt install vim
```
PPA found here: [https://launchpad.net/~jonathonf/+archive/ubuntu/vim](https://launchpad.net/~jonathonf/+archive/ubuntu/vim)
He maintains his PPA's very nicely.

---

### Post by deadflowr on 2019-07-27
You should be able to just add the epoch to the beginning of the version string.
Make it something higher than 2
So where the original string is 2:12345 make it 3:12345

FWIW with checkinstall you can give it any version string you want, really.
If you want to give the string 9:999, then you can.

(Note the epoch is just the number before the colon.
With the epoch it assumes the epoch number is zero)

---

### Post by frrobert on 2019-07-27
Thank you both for your answers.

---

