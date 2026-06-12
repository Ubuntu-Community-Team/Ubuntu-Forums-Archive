---
title: "Error: No package called &quot;flashplayer-mozilla&quot;"
date: 2005-04-12
forum: General Help
---

### Post by computerdude33 on 2005-04-12
Is there a way to install Flash Player on Firefox?

---

### Post by Klin'Targ on 2005-04-12
You have to add additional sources to your /etc/apt/sources.list file to see the flashplayer-mozilla package. 
For detailed instructions on how to do this and many other nice things, see the [Ubuntu Starter Guide](http://www.ubuntuguide.org#repositories)

---

### Post by computerdude33 on 2005-04-12
Thanks!

---

### Post by computerdude33 on 2005-04-12
Yeah... um...

 [QUOTE=Terminal]@ubuntu:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package flashplayer-mozilla
[/QUOTE]

---

### Post by Klin'Targ on 2005-04-12
Hmm... Make sure you have them listed in the form ```
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
``` making sure there is no "/" between hoary and universe.

Another possibility:
Did you run the commands at the bottom after adding the repos? (The guide doesn't make it totally clear that this is required)```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update
```

---

