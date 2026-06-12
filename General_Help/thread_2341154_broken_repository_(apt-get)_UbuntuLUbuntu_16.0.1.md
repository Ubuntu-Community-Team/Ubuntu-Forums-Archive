---
title: "broken repository (apt-get) Ubuntu/LUbuntu 16.0.1"
date: 2016-10-25
forum: General Help
---

### Post by ice-simx on 2016-10-25
For ubuntu/lubuntu 16.0.1 the repositories seems broken. As unable to do 'apt-get update' and use synaptic in lubuntu.
Keep on getting errors
     - unresolved dependency PKG depend on PKG-B.x but PKG-B.y is going to install. Installation cannot continue
     - signature verification error. unable to fetch InRelease file.

this is frustrating. tried all methods, like recreating source.list using other country mirrors, main server But nothing is working.
I'm able to access the link using web-browser, but apt-get unable to do so :(

---

### Post by QIII on 2016-10-25
Hello!

Would you please copy and paste the entire output of the terminal when you attempt to update?

Please use code tags.

Thanks.

---

### Post by ice-simx on 2016-10-25
Hello,
Following is the output:

```

root@LXDE:~# uname -a
Linux LXDE 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


root@LXDE:~# grep -v "^#" /etc/apt/sources.list

deb http://archive.ubuntu.com/ubuntu xenial main universe


root@LXDE:~# apt-get update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Reading package lists... Done
root@LXDE:~# apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vim : Depends: vim-common (= 2:7.4.1689-3ubuntu1) but 2:7.4.1689-3ubuntu1.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by ice-simx on 2016-11-01
Problem solved :)

Upon checking I found that vim-common was already installed (may be default with installation of Lubuntu 16.04.1).
I uninstall the "vim-common 2:7.4.1689-3ubuntu1.1" along with it "ubuntu-minimal" got uninstalled, i took the chance.

Then i install vim, which installed successfully this time along with "vim-common" :)

My analysis is that, it seem the default packages are of higher version than available/depended in repositories.
Like, in this case vim depend on vim-common...3ubuntu1 but vim-common...3ubuntu1.1 was installed by-default with OS installation.

Hope it will be helpful for someone.

---

### Post by ice-simx on 2016-11-01
PS: Following is my current source.list file and I also added [arch=amd64]
```

# grep -v "^#" sources.list

deb [arch=amd64] [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [arch=amd64] [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main universe multiverse restricted
deb [arch=amd64] [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main universe multiverse restricted

```

---

