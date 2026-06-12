---
title: "ssh  /initrd.img: cannot execute binary file"
date: 2018-06-21
forum: General Help
---

### Post by mrkkbb on 2018-06-21
Hello all,

I'm having an issue with trying to ssh into my machine running 18.04LTS with 4.15.0-23.25-generic 4.15.18 with OpenSSH_7.6p1 Ubuntu-4, OpenSSL 1.0.2n

I get the following after the splash screen.  There is a delay of about 30 seconds then this and I'm kicked out:

Last login: Thu Jun 21 16:25:24 2018 from  ip
-bash: source: /initrd.img: cannot execute binary file
-bash: source: /initrd.img.old: cannot execute binary file
-bash: /vmlinuz: Permission denied
-bash: /vmlinuz.old: Permission denied
Connection to ip closed.

If i do ctrl-c during the pause, I am able to get in.

Thanks
R

---

### Post by steeldriver on 2018-06-21
It looks like you have messed up at least one of your login shell's initialization files:

```

/etc/profile
~/.bash_profile
~/.bash_login
~/.profile
~/.bashrc

```

(the latter being sourced from ~/.profile - at least in the default Ubuntu implementation)

---

### Post by mrkkbb on 2018-06-26
Thanks! That was it. I copied over a script to set-up environment for an installed software into /etc/profile.d that had a bug in it.

---

