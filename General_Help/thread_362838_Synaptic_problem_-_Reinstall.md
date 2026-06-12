---
title: "Synaptic problem - Reinstall?"
date: 2007-02-16
forum: General Help
---

### Post by OrangeCrate on 2007-02-16
After using the instructions to enable additional repositories from the tutorial listed below that I found in another thread, I ended up with numerous errors telling me that I had duplicate respositories.

"Originally Posted by aysiu - If you prefer to do everything the point-and-click way, this link may serve you better: http://www.monkeyblog.org/ubuntu/installing"

I went back into synaptic to remove the changes, and I accidently deleted the following as I was editing:

"Ubuntu 6.06 (Source)
Officially supported.
Restricted copyright."

And frankly, I am not sure that I have changed everything back to the way it was, as I have been unable to find a list of the default settings to compare against.

I'm not sure of what to do next - any help would be appreciated.

---

### Post by erkki70 on 2007-02-16
Hi,
In terminal, type:
```
 gksudo gedit /etc/apt/sources.list
```
and remove or comment (add # at the beginning of the lines) the entries.
Alternatively you could use:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
and generate a customized to your needs new sources.list file and replace it in /etc/apt/ folder.

Hope this helps...

Cheers,

---

### Post by OrangeCrate on 2007-02-16
> **erkki70 said:**
> Hi,
In terminal, type:
```
 gksudo gedit /etc/apt/sources.list
```
and remove or comment (add # at the beginning of the lines) the entries.

Alternatively you could use:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
and generate a customized to your needs new sources.list file and replace it in /etc/apt/ folder.


I'm sorry, being fairly new to Ubuntu, I'm a bit confused. When I typed in your instruction at the terminal, I got this:

gksudo gedit /etc/apt/sources.list
(gedit:8888): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

But, it did give me this output:

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

As instructed, I should remove the #s? Do I add a # to the lines that do not have them?

---

As it relates to your second suggestion, it was easy to generate the custom list (I believe this is what I would need?), but I'm not sure how to install it in the /etc/apt/ folder.

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

Could you explain further?

---

### Post by OrangeCrate on 2007-02-16
Anyone?

---

### Post by erkki70 on 2007-02-16
Hi, 
If you want to use the generated list, follow the instructions to add the key:
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
```then
```
gpg --export --armor KEY | sudo apt-key add -
```where KEY is eg. 437D05B5

Then you need to edit your sources.list so:
```
 gksudo gedit /etc/apt/sources.list
```and copy paste replace all with the generated sources.list
```

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

```
Save and close Gedit.
Now type:
```
sudo apt-get update
```or launch synaptic and hit the top left button to reload sources.
That's it :-)

---

### Post by OrangeCrate on 2007-02-16
> **erkki70 said:**
> Hi, 
If you want to use the generated list, follow the instructions to add the key:
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
```then
```
gpg --export --armor KEY | sudo apt-key add -
```where KEY is eg. 437D05B5



I don't want to screw up things anymore than I have, so, to be cautious, am I correct then that the first two instructions would read:

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 437D05B5

gpg --export --armor 437D05B5 | sudo apt-key add

Edit:

Nevermind, I think I understand it, and will post back my results. Thanks...

---

### Post by OrangeCrate on 2007-02-16
> **erkki70 said:**
> Hi, 
That's it :-)

Your instructions worked perfectly, thank you for your help!

OC

---

