---
title: "apt-update signature invalid"
date: 2007-10-23
forum: General Help
---

### Post by thhjimmy on 2007-10-23
HI,
any idea what should I do if apt-get update have this error?
:popcorn:



W: GPG error: [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Duplicate sources.list entry cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Packages (/var/lib/apt/lists/Ubuntu%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071016.1)_dists_gutsy_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Packages (/var/lib/apt/lists/Ubuntu%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071016.1)_dists_gutsy_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by Tickle Me Elmo on 2007-10-27
Hi, I found this while googling - which might help you [[link]("http://members.shaw.ca/Limulus/feisty.html")]

---

### Post by komputes on 2008-03-05
This doesn't happen very often, but when it does you should run these two commands to get the valid GPG keys which apt-get uses to validate that the  package you are downloading, or server you are communicating with is authentic. 

```

GPGKEY= <place the GPG key from /etc/apt/sources.list here>
gpg --keyserver hkp://subkeys.pgp.net --recv-keys $GPGKEY
gpg --export --armor $GPGKEY | sudo apt-key add -
```

You need to replace $GPGKEY with the key in the error message or sources.list (not all sources.list have this).

These keys can also be seen by going to System > Administration > Synaptic Packet Manager > Settings Menu > Repositories > Authentication

You can try clicking on Restore Defaults if you never had this problem before.

For more information on PGP look here:
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

---

### Post by shaggy999 on 2008-04-04
I have this same problem that popped up today and the fix suggested does not work. When I run teh first command on the gpgkey it says the key was never changed.

Here's the error message when I apt-get update

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by babecek on 2008-04-15
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -

---

### Post by vnevoa on 2008-04-29
Hi. 
I stumbled upon this error too, after installing Hardy fresh in a Mac G3.
The Mac was connected to the Internet via a defective Ethernet cable, and lost most of the IP packets, but some got through with corrupted data.
As a result, my "apt-get updates" corrupted the apt system, and this thread's error started happening. Only after that I noticed the cable problem.

I did all that is described in this thread, as well as many others, and even some other stuff I desperately invented.
In the end, what solved the problem was:
1 - remove the offending repository from the "sources.list";
2 - do "apt-get update";
3 - insert the offending repository back into the "sources.list";
4 - do "apt-get update" again; it should be working now.

Other stuff I did before:
- sudo apt-get --reinstall install apt; # had the cd-rom in the sources.list;
- sudo apt-key remove 437D05B5; # to remove the offending key;
- sudo apt-key update; # to reinstall the offending key;

But as I said, it was only after tricking apt-get's cache system that things started working again.

Hope this helps someone.

---

