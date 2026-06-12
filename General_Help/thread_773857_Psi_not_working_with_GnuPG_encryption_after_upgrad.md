---
title: "Psi not working with GnuPG encryption after upgrade to 8.04"
date: 2008-04-29
forum: General Help
---

### Post by His Eminence on 2008-04-29
Hi!

Psi stopped to work with GnuPG after upgrade to 8.04. 

Problem is weird - I'm using a Jabber server that requires TLS/https encrypted connection. If I select the key to use with GnuPG encryption in the account configuration dialog I can't connect to server - the star icon pulses and it tries to connect but without success. If I unselect the GnuPG it connects ok.

It was OK before the upgrade on the old system (7.10) with both encrypted and unencrypted chats working flawlessly. Now I can't use encryption because Psi won't connect with the server if GnuPG key is selected. 

Any clues?

---

### Post by lkraemer on 2008-05-03
His Eminence,
Perhaps my post at:
[http://ubuntuforums.org/showthread.php?t=780970&highlight=PSI+with+Ubuntu+8.04](http://ubuntuforums.org/showthread.php?t=780970&highlight=PSI+with+Ubuntu+8.04)

will help.  I got it working on Ubuntu 8.04 LTS.

LK

---

### Post by His Eminence on 2008-05-05
Thanks for replying, however your solution works with Google's server and the crux of my problem is GnuPG encryption not working (hence no GnuPG encrypted chats anymore for me). 

But my Mac returned from the repair shop today, which basically should solve my problems.

---

### Post by IamAcoconut on 2008-06-28
Did you solve this issue? The problem is not with the connection itself obviously - it is that PSI wants you to enter your openPGP passphrase before even attempting to connect to server, so  that any encrypted messages that might be awaiting you are deciphered instantly. 

It must be the password entry GUI that's at fault. This reminds me of an issue with thunderbird-enigmail which required the package 'pinentry-*' to be able to display the GPG passphrase entry dialog. Yet I don't know what package we need here.

---

