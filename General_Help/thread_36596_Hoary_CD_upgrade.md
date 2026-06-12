---
title: "Hoary CD upgrade"
date: 2005-05-23
forum: General Help
---

### Post by jasmuz on 2005-05-23
](*,) My system is a Warty upgraded to Hoary, running the latest Synaptic.
I also run the Ubuntu backports without a hitch!
Thing is ...today i recieved my first Hoary cd's...i wanted to add it to the repositories in order to save my self the download time of the Xorg and other programs.

And i get this error when i try to add the cd

This disc is called:
'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
Copying package lists...gpgv: Signature made Wed 06 Apr 2005 11:30:36 PM AST using DSA key ID FBB75451
gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/hoary/Release.gpg

Can anybody help?...
Thanks anyways

---

### Post by cjwatson on 2005-05-27
[QUOTE=jasmuz]](*,)
Copying package lists...gpgv: Signature made Wed 06 Apr 2005 11:30:36 PM AST using DSA key ID FBB75451
gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/hoary/Release.gpg
[/QUOTE]
 gpg --keyserver subkeys.pgp.net --recv-keys FBB75451

(Don't get into the habit of doing this for just any key verification error; if you don't expect it, it may be an attempt to compromise your system. However, in this case, I'm assuming you're willing to trust the physical CD you've received.)

---

### Post by jasmuz on 2005-05-28
[QUOTE=cjwatson]gpg --keyserver subkeys.pgp.net --recv-keys FBB75451

(Don't get into the habit of doing this for just any key verification error; if you don't expect it, it may be an attempt to compromise your system. However, in this case, I'm assuming you're willing to trust the physical CD you've received.)[/QUOTE]
 I tried that...and got this:

jasmuz@serenity:~ $ sudo  gpg --keyserver subkeys.pgp.net --recv-keys FBB7545
Password:
gpg: WARNING: unsafe ownership on configuration file "/home/jasmuz/.gnupg/gpg.conf"
gpg: skipping invalid key ID "FBB7545"

and then this:

jasmuz@serenity:~ $ sudo  gpg --keyserver subkeys.pgp.net --recv-keys fbb75451
gpg: WARNING: unsafe ownership on configuration file "/home/jasmuz/.gnupg/gpg.conf"
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


any ideas?...i just found the hole issue quite strange..

---

