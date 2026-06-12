---
title: "is there a way to run an Ubuntu system w/o PAM?"
date: 2019-04-29
forum: General Help
---

### Post by Skaperen on 2019-04-29
is there a way to run an Ubuntu system without PAM?

PAM has been a troublemaker, too often prompting for a password in non-interactive situations, causing some scripts to never complete.  piping in a password does work ... it apparently opens /dev/tty directly.  when i tried to purge PAM packages, apt-get detected this would remove essential packages.  i tried all 7 PAM packages individually and 4 of them cause this issue.  it looks like quite a lot of the system is built to depend on PAM.

alternatively, is there a way to configure PAM to be more sane and read stdin?

---

### Post by Rubi1200 on 2019-05-01
I don't know if it is possible to say without PAM since it is tightly integrated into most modern distros.

But I think this guide might be a good starting point:
[https://www.tecmint.com/configure-pam-in-centos-ubuntu-linux/](https://www.tecmint.com/configure-pam-in-centos-ubuntu-linux/)

---

### Post by Skaperen on 2019-05-01
looks like i would need to rebuild everything to not include libpam.so (perhaps lots of source patches).  it could be easier to just resolve the tty prompt issue.  but the linked article doesn't cover this issue.  it is probably something in libpam.so doing it, but maybe their is a config option to tell it how to detect that no one is home.  the prompt should at least have some kind of timeout and a way to read from provided credentials instead of the tty.

---

### Post by HermanAB on 2019-05-01
Hmm, my guess is that the problem is not with PAM. 

You need to take the dear lady a bunch of flowers and learn how to live with her.

---

### Post by Skaperen on 2019-05-02
what knowledge and/or experience makes you guess that the problem is *not* with PAM?

my definition of the *problem* is that there is no (documented) means to either pipe input into the password prompt (the tty it opened and is waiting for input from) or inform PAM that there can be no input and that it should not open and read the tty for an infinite/long period of time.  i see no reason PAM should not have this capability for any and all cases where it would prompt for a password.  maybe a standardize environment variable name to inform any code, such as TTY_NOT_REAL=1 could be used.

at least in the case i recently ran into this, there is a way to accomplish my need without using any "PAM-aware" executables.  but, there could be future tasks where such a means does not exist.  if PAM was better "TTY-aware" i might be inclined to make programs i write be "PAM-aware" where authentication can be of value.

reading the linked TecMint article confirmed my belief that the problem *is* with PAM.

---

