---
title: "Can't install video repositories to play dvds on ubuntu 12.04 32 bit"
date: 2013-10-12
forum: General Help
---

### Post by Aric_ on 2013-10-12
Hey gusy I have run into an issue that I can't seem to find a solution for. I just installed ubuntu 12.04 32 bit and tried to install the repositories or codes (not sure what to call them) to play encrypted dvds. I used the codes below and when I run them, the first one works fine, but the second one gives me the message that is below the second code. I tried to find the medibuntu.org and there is a message that says that it is no longer being used, so where do I get the codecs/repositories to play encrpyted dvd's, because I can't seem to find it anywhere else. Thanks. :confused:

sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh

Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'

---

### Post by philinux on 2013-10-12
Yep. The maintainer of medibuntu has quit. [https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)

There is another way now. [http://howtoubuntu.org/how-to-play-a-dvd-in-ubuntu#.UlmAVXhCK3c](http://howtoubuntu.org/how-to-play-a-dvd-in-ubuntu#.UlmAVXhCK3c)

---

### Post by philinux on 2013-10-15
The bug has now been fixed.

[https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/1223928](https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/1223928)

---

### Post by deadflowr on 2013-10-15
Yep, as stated above it has been fixed.
Open the update manager and if it doesn't have any updates(the update you should see if it does is for libdvdread4)
then run "check"
And, it should go without saying, install the update.

---

