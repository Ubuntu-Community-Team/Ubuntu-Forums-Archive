---
title: "W32codecs in any repo?"
date: 2005-10-12
forum: General Help
---

### Post by Panthios on 2005-10-12
Hi.

Is W32codecs gone from the repo's?

Is my sources.list ok, to get the most software?

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
```

---

### Post by Pablo_Escobar on 2005-10-12
Yep, gone, and they won't be back - legal issues, look for the link in the how-to section of this forum.

---

### Post by Irony on 2005-10-12
I couldn't get the w32 codecs for some months and then one day they mysteriously popped up in the repos so I installed them via synaptic. I guess I was lucky.

---

### Post by Hairy_Palms on 2005-10-12
type "sudo gedit" in a terminal and add the line below 


Code:	
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main	

apt-get update 
then apt-get the w32 codecs and libdvdcss and whatever else to playback stuff

---

