---
title: "[multiarch] openssl update is preventing all apt/dpkg installations"
date: 2014-05-10
forum: General Help
---

### Post by JamesNorris on 2014-05-10
I know this has been posted elsewhere. both recently and long ago, but the solutions in posts
[like this]("http://askubuntu.com/questions/167784/how-to-resolve-e-internal-error-when-using-apt-get-remove") just don't help. 

trying to install anything with dpkg or apt (or synaptic) gives me this error:
```
 package libssl1.0.0:amd64 1.0.1-4ubuntu5.13 cannot be configured because libssl1.0.0:i386 is at a different version (1.0.1-4ubuntu5.12)
dpkg: error processing libssl1.0.0:i386 (--configure):
 package libssl1.0.0:i386 1.0.1-4ubuntu5.12 cannot be configured because libssl1.0.0:amd64 is at a different version (1.0.1-4ubuntu5.13)
Errors were encountered while processing:
 libssl1.0.0:amd64
 libssl1.0.0:i386

```

Manually downloading the i386 version of libssl1.0.1-4ubuntu5.13 gives me a
```
dpkg: error processing libssl1.0.0_1.0.1-4ubuntu5.13_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
```
error

There seem to be a couple of bugs many years old in the lauchpad for openssl around this, but they've not been looked at by devs by the look of things. 

Any solution here would be greatly accepted.

---

### Post by SeijiSensei on 2014-05-10
Why are you trying to install packages for both architectures?  The second error message says you're on an amd64 system trying to install an i386 package.

Second, why are you trying to install OpenSSL from some .deb when you can use 
```
sudo apt-get install openssl
```
If you're worried about the Heartbleed bug, that was fixed in Ubuntu's OpenSSL packages within hours of the release of the patch.

---

### Post by JamesNorris on 2014-05-10
I have no idea for the first question because the answer to the second is that this is an update to already installed packages, prompted by the Update Manager about a week ago.

---

### Post by JamesNorris on 2014-05-13
Update; not sure if this helps, though. 

I've done an apt-get clean; apt-get update and then force-installed with dpkg all of the apt cache .deb files. As expected, it crashed out without configuring and here is the output of dpkg --configure -a

```
sudo dpkg --configure -a
dpkg: error processing libssl1.0.0:amd64 (--configure):
 package libssl1.0.0:amd64 1.0.1-4ubuntu5.13 cannot be configured because libssl1.0.0:i386 is at a different version (1.0.1-4ubuntu5.12)
dpkg: error processing libssl1.0.0:i386 (--configure):
 package libssl1.0.0:i386 1.0.1-4ubuntu5.12 cannot be configured because libssl1.0.0:amd64 is at a different version (1.0.1-4ubuntu5.13)
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl1.0.0 (>= 1.0.1); however:
  Package libssl1.0.0:amd64 is not configured yet.
```

There are 27 other packages that this is leaving unconfigured as well.

---

### Post by JamesNorris on 2014-05-13
Mind you, I'm not sure where the multiarch thing comes in here, as apt-cache policy gives this:

```
apt-cache policy libssl1.0.0:i386N: Unable to locate package libssl1.0.0:i386
N: Couldn't find any package by regex 'libssl1.0.0'

```

---

