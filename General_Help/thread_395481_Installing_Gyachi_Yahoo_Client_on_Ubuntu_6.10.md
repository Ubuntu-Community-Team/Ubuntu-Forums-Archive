---
title: "Installing Gyachi Yahoo Client on Ubuntu 6.10"
date: 2007-03-28
forum: General Help
---

### Post by Dream. on 2007-03-28
Hello, first of all this is my first post here on the Ubuntu forums so I would like to say hi to everyone.

I Have just installed Ubuntu 6.10 I believe this is Edgy? can someone verify that for me.

Ok. When trying to install gyachi_1.0.5-1_edgy_i386.deb I am getting the following msg...

Error: Dependency is not satisfiable: libmcrypt4

Does anyone know where I can get this file from? My searches have failed to locate anything on this file or any similar problem in these forums.

Thankyou.

P.S. Have i posted this in the right forum?

---

### Post by fanatik on 2007-03-28
Simple:

Type this in a termina:

**sudo aptitude install libmcrypt4**

Enter your password when requested.

Done :)

---

### Post by Dream. on 2007-03-28
Thanks fanatik for a quick response!

I got the following msg when executed (along with a heap of other jargon)

Couldn't find any package whose name or description matched "libmcrypt4"

Any ideas as to why the package was not available?:confused:

---

### Post by fanatik on 2007-03-28
Probably because your sources aren't fully set up - can you paste the output of:

cat /etc/apt/sources.list

Cheers,
James.

---

### Post by Dream. on 2007-03-28
cat /etc/apt/sources.list

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by qwerty12 on 2007-03-28
If you are feeling lazy, get Automatix to do it for you :)

---

### Post by fanatik on 2007-03-28
so you just need to run:

gksudo gedit /etc/apt/sources.list

and uncomment the lines:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

ie take the # off the front
Save and exit, then type:

sudo aptitude update

and try the install command again.

---

### Post by Dream. on 2007-03-28
Sorry for the delay, I had update manager running.

Ok, thankyou very much fanatik :) , all went well and Gyachi has installed without errors.

To my understanding Synaptics lists the programs I have installed?

Now all I need to do is work out how to run them!!

Thanks once again for your help fanatik.

---

