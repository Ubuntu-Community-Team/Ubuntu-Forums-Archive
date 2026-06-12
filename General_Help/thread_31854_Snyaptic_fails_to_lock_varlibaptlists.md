---
title: "Snyaptic fails to lock /var/lib/apt/lists"
date: 2005-05-05
forum: General Help
---

### Post by stardotstar on 2005-05-05
I usually use apt-get when on my broadband - but from work I need to use Synaptic because it lets me configure a proxy...

Since upgrading to Hoary I now get this message when I try to update my repositories:

```

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

```

I can browse to the directory and everything seems to be present and available.

```
root@gecko:/var/lib/apt/lists # ls
archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_hoary_Release
archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_hoary_universe_source_Sources
lock
partial
security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_hoary-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_hoary-security_Release
security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_hoary-security_restricted_source_Sources
root@gecko:/var/lib/apt/lists # vi lock
root@gecko:/var/lib/apt/lists # ls -l lock
-rw-r-----  1 root root 0 2005-05-05 15:57 lock

```

Can anyone enlighten me as to what is happening here please?

---

### Post by Psquared on 2005-05-05
Do you have apt-get open in a terminal? This message usually means that another application already has a lock on the cache. It might also be a permissions issue. When did this start?

---

### Post by stardotstar on 2005-05-05
[QUOTE=Psquared]Do you have apt-get open in a terminal? This message usually means that another application already has a lock on the cache. It might also be a permissions issue. When did this start?[/QUOTE]
 Thanks for the tip:  I am away from the server right now and I will investigate this asap and get back to you.  It seems to have happened sometime after upgrading to Hoary...

I doubt that I had apt-get running in any capacity since I can't use it with the proxy on the work lan.  So somehow perhaps a lock has been left on by a previous session (is that possible) how can I tell?

As for permissions - I have enabled the root account on this system but with Synaptic I use the regular user sudo password when invoking the app in Gnome.

Cheers,
Will

---

### Post by talkingwires on 2005-06-18
I had an issue similar to yours this morning. It turned out that the System Notifier was busy checking for updates and had a lock on the apt package list while it worked. I guess it usually checks at bootup, but I'd had my ASDL cord unplugged and it kept a lock on the list until I plugged it back it. I don't know if this was a bug or a feature... :???:

---

### Post by Seer on 2005-06-21
[QUOTE=stardotstar]I usually use apt-get when on my broadband - but from work I need to use Synaptic because it lets me configure a proxy...

Since upgrading to Hoary I now get this message when I try to update my repositories:

```

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

```

I can browse to the directory and everything seems to be present and available.

```
root@gecko:/var/lib/apt/lists # ls
archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_hoary_Release
archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_hoary_universe_source_Sources
lock
partial
security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_hoary-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_hoary-security_Release
security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_hoary-security_restricted_source_Sources
root@gecko:/var/lib/apt/lists # vi lock
root@gecko:/var/lib/apt/lists # ls -l lock
-rw-r-----  1 root root 0 2005-05-05 15:57 lock

```

Can anyone enlighten me as to what is happening here please?[/QUOTE]
 Ctrl + Alt + Backspace normally clears this up for me :)

---

