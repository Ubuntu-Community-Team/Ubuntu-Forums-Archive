---
title: "[Kubuntu Gutsy] Kopete doesn't work at all"
date: 2007-10-19
forum: General Help
---

### Post by Crakie on 2007-10-19
I upgraded to Gutsy today. Everything seems to remain in working order, except  Kopete. When I start it, the icon appears in the tray, but the program is not functioning at all. Meanwhile, the CPU load by the Kopete process goes to 100 % (leaving my other core to do all the work ;)) and the only way out is to kill it.

I am aware of the bug connecting to MSN, but this seems unrelated (and the fix does not help at all). Any ideas?

---

### Post by Tomasu82 on 2007-10-20
I'm having a similar problem, except it just crashes on startup.

---

### Post by fragility14 on 2007-10-20
edit: I have nothing to add with this post and it will not let me delete it.

---

### Post by falcon15500 on 2007-10-20
Same here... When I try Kopete it asks me for my password (as normal) but then bombs out to the KDE crash handler with "The application Kopete (kopete) crashed and caused the signal 11 (SIGSEGV)."  I might try to downgrade versions, or compile from sources.  Will update when I have results.

falc

Edit:  It's a kdelibs problem - and a fix has been posted [http://ubuntu.lnix.net/misc/kdelibs4c2a_3.5.8-0ubuntu3_i386.deb]("http://ubuntu.lnix.net/misc/kdelibs4c2a_3.5.8-0ubuntu3_i386.deb")

Although the above apparently doesn't help the OP.  Sorry!

---

### Post by GearStick on 2007-10-20
I have the same problem since I updated the kdelibs. After starting kopete connects for a Second and then dies. Tested it on a 64 bit and a 32 bit system.


 kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
QFont::setPointSize: Point size <= 0 (-1)
QGDict::hashKeyString: Invalid null key
QGDict::hashKeyString: Invalid null key
kopete: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol ''.
kopete: 
KCrash: Application 'kopete' crashing...
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3600053
kio (KIOConnection): ERROR: Could not write data
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3601044
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3601044
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x3601044

---

### Post by Crakie on 2007-10-20
Hmmm, I guess we should file a bugreport. Unfortunately, I don't have any debug info to offer. If I start Kopete from terminal, it exits without any error message.

---

### Post by krazyman on 2007-10-20
I got the same...

---

### Post by Crakie on 2007-10-20
I found a bugreport [here]("https://bugs.launchpad.net/ubuntu/+source/kopete/+bug/154243"). Please post any relevant info if you are experiencing similiar problems.

---

### Post by ekred on 2007-10-20
A i386 fix can be downloaded [*[COLOR="DarkOrange"]here[/COLOR]*]("http://kubuntu.org/~jriddell/kdelibs4c2a_3.5.8-0ubuntu3_i386.deb").
That link is coming from [*[COLOR="DarkOrange"]this page[/COLOR]*]("http://www.kdedevelopers.org/node/3041").
Worked well with me! 8)

---

### Post by Tomasu82 on 2007-10-20
Perfect, that worked great. :) thanks to everyone who had a hand in fixing it and bringing that deb to my attention :)

---

### Post by vratnica on 2007-10-20
> **ekred said:**
> A i386 fix can be downloaded [*[COLOR="DarkOrange"]here[/COLOR]*]("http://kubuntu.org/~jriddell/kdelibs4c2a_3.5.8-0ubuntu3_i386.deb").
That link is coming from [*[COLOR="DarkOrange"]this page[/COLOR]*]("http://www.kdedevelopers.org/node/3041").
Worked well with me! 8)


emm, would you be so kind to explain how I can use these informations to actually fix the problem?

I downloaded the fix file but I dont know what further to do?

Thanx!

---

### Post by Tomasu82 on 2007-10-20
> **vratnica said:**
> emm, would you be so kind to explain how I can use these informations to actually fix the problem?

I downloaded the fix file but I dont know what further to do?

Thanx!
```
dpkg -i kdelibs4c2a_3.5.8-0ubuntu3_i386.deb
```

Or something along those lines :) I think the GUI programs also let you select deb files.

---

### Post by vratnica on 2007-10-21
Thank you very much!

=D>

---

### Post by GearStick on 2007-10-21
After the last Update from the gutsy-sources everthing works fine again. :-)
But thanks for the fix.

---

### Post by MarcRJacobs on 2007-12-18
I am having the same problem with Kopete on Gutsy.  I downloaded the .deb file and tried to install it.  The installed reported, "Error: A later version is already installed".  Any recommendations on how I can fix this would be appreciated.
Thanks

---

### Post by evil_cat on 2008-05-11
the link does not work

---

### Post by evil_cat on 2008-05-11
This is due to the bug 153500 in the kdenetwork

[https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/153500](https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/153500)

You need to download
kdelibs4c2a_3.5.8-0ubuntu3_i386.deb

You can try to download it
sudo apt-get install kdelibs4c2a

If you cannot do it add the following repository
sudo gedit /etc/apt/sources.list
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

---

