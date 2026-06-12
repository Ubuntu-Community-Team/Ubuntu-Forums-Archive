---
title: "ubuntu-keyring broken (error 127)"
date: 2012-12-03
forum: General Help
---

### Post by jktjs on 2012-12-03
My kubuntu 12.04 system is running fine but I have not been able to install updates for a while. Switching to the UK update server has allowed me to compile a list of updates, but I am not able to install them. The problem fundamentally seems to be a broken ubuntu-keyring and I am not able to reinstall it.

In the muon packaga manager I tried to reinstall it and got:

```
Package: ubuntu-keyring
Error: subprocess installed post-installation script returned error exit status 127

```

Running this in the command line:

```
sudo apt-get install --reinstall ubuntu-keyring
```

gives:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 484 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up ubuntu-keyring (2011.11.21.1) ...
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP
dpkg: error processing ubuntu-keyring (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 ubuntu-keyring
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Trying 
```
sudo dpkg-reconfigure ubuntu-keyring 
```

gives

```
/usr/sbin/dpkg-reconfigure: ubuntu-keyring is broken or not fully installed. 
```

Advice appreciated!

---

### Post by SeijiSensei on 2012-12-03
For some reason it is looking in /usr/local/lib for libreadline.  Did you install a different version of the library there or install a version of gpg besides the one in the repositories?  /usr/local is generally empty on a default installation.  If you compiled something from source, it usually installs under /usr/local, but otherwise there should not be anything there.

You can try running "sudo ldconfig", but I'm not sure that will help.

---

