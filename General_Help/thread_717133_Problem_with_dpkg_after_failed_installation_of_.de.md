---
title: "Problem with dpkg after failed installation of .deb package"
date: 2008-03-06
forum: General Help
---

### Post by jaimeloza on 2008-03-06
Hello everyone,

I am a new user to Ubuntu Gutsy and I am having a problem with a faild installation of the limewire-basic.deb package.
After trying to install it, my system  locked-up in the process, so I had to restart Ubuntu.
After this, I can not install any new packages or updates.

When I try to do this I get a window that tell me that "dpkg' is still running and that I have to enter a manual command "dpkg --configure -a" to finish the sesion or something like that.

Can anyone tell me how can I restore or remove a failed package installation using dpkg?

I have tried all the commands that I was able to fine underthe help menu but nothing works. Sometimes I get a message that the actions require a superuser level or smething similar.

Thank you,

---

### Post by taurus on 2008-03-06
Open a terminal and run these commands.  Post the outputs here.

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

Use the same password that you log in with.

---

### Post by jaimeloza on 2008-03-07
Thank you for your replay, I will try that and let you know.

---

### Post by jaimeloza on 2008-03-07
Thakns again, it looks like that solve my problem. There is one more thing I would like to ask you, is there a command that I can use to remove or repair a broken package?

After running the commands you ask me to, I got an error updating an application called Automatix that I loaded thinking that it will make the installation of packages in Ubuntu a lot easier.

Thank you again.

---

### Post by jaimeloza on 2008-03-07
This is what I got from at the end of the terminal screen after I run the last command "sudo apt-get uipdate"

Err [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg                              
  Could not resolve 'www.getautomatix.com'
Err [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_US
  Could not resolve 'www.getautomatix.com'
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages
Err [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages
  Could not resolve 'www.getautomatix.com'
Fetched 421kB in 5m36s (1251B/s)        
Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/Release.gpg](http://www.getautomatix.com/apt/dists/gutsy/Release.gpg)  Could not resolve 'www.getautomatix.com'
Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/main/i18n/Translation-en_US.bz2](http://www.getautomatix.com/apt/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not resolve 'www.getautomatix.com'
Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/Packages.gz)  Could not resolve 'www.getautomatix.com'
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jaime@Linux-Desktop:~$

---

### Post by taurus on 2008-03-07
First, you can only run one process, adept, at a time.  So, if you have Add/Remove, Synaptic, or update-manager, you cannot run apt-get from a terminal.  

Second, you should consider removing automatix because there is your problem.  But if you still insist on using automatix, then good luck.

---

### Post by jaimeloza on 2008-03-11
Thank you once again for your help and insights to my problem. I am still working on trying to remove Automatix. I was hoping to be able to use it to install packages in a simpler way after reading about it but so far it has not worked yet.

Jaime.

---

