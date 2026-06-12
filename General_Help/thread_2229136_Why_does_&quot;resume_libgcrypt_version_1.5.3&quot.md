---
title: "Why does &quot;resume: libgcrypt version 1.5.3&quot; appear at boot?"
date: 2014-06-11
forum: General Help
---

### Post by scott092707 on 2014-06-11
Everytime I boot since I installed Lubuntu 13.04, I get the above message in the upper left corner of the screen.

It stays there, goes bold for a while, and then, just before the boot continues to the login screen, it goes back to un-bold.

The booting otherwise seems fine.

Libgcrypt appears to have something to do with hibernation/suspension, but I do not do that (I have tuxonice, but have not gotten it to work in a while, and have not put in the effort needed to fix the situation).

I am just curious why the message is there...

---------------------
scott@scott-AsusM2N68-AM-Plus:~$ uname -a
Linux scott-AsusM2N68-AM-Plus 3.13.0-29-generic-tuxonice #53~ppa1-Ubuntu SMP Fri Jun 6 17:27:38 UTC 2014 i686 athlon i686 GNU/Linux
scott@scott-AsusM2N68-AM-Plus:~$ lsb_release -dsc
Ubuntu 14.04 LTS
trusty
scott@scott-AsusM2N68-AM-Plus:~$ echo $DESKTOP_SESSION
Lubuntu



-Scott

---

### Post by bapoumba on 2014-06-12
> **scott092707 said:**
> Everytime I boot since I installed Lubuntu 13.04, I get the above message in the upper left corner of the screen.
..


May be here : [https://bugs.launchpad.net/ubuntu/+source/libgcrypt11/+bug/665932](https://bugs.launchpad.net/ubuntu/+source/libgcrypt11/+bug/665932)
May I just say that 13.04 has reached end of life last january and it would be better to run a supported release.

---

### Post by scott092707 on 2014-06-12
Sorry, I seem to have mis-typed:  I use Lubuntu 1_***4***_.04.

I may try the fix your link suggested...

It seems to suggest that the computer thinks it is resuming a hibernated/suspended session, and then (sometimes) goes ahead and boots normally after a (sometimes lengthy) delay...

-Scott

---

### Post by scott092707 on 2014-06-13
In "[https://bugs.launchpad.net/ubuntu/+s...11/+bug/665932]("https://bugs.launchpad.net/ubuntu/+source/libgcrypt11/+bug/665932")",
 it says to "Edit the file /usr/share/initramfs-tools/hooks/resume"
but that file does not exist...
There is some Tuxonice stuff there, but I find nothing about "autodetect" that I could comment out,
and I have not been hibernating anyway....

---

### Post by bapoumba on 2014-06-13
Sorry :)
I'll have to look again then.

---

### Post by bapoumba on 2014-06-14
There is little info I can find with this error. Please check if you have something similar to this :
```
apt-cache search libgcrypt
libgcrypt11 - LGPL Crypto library - runtime library
libgcrypt11-dbg - LGPL Crypto library - debugger files
libgcrypt11-dev - LGPL Crypto library - development files
libgcrypt11-doc - LGPL Crypto library - documentation
libgpg-error-dev - library for common error values and messages in GnuPG components (development)
libgpg-error0 - library for common error values and messages in GnuPG components
libcrypt-gcrypt-perl - Perl interface to the GNU Cryptographic library
libcrypto++-dev - General purpose cryptographic library - C++ development
libcrypto++-doc - General purpose cryptographic library - documentation
libcrypto++-utils - General purpose cryptographic library - utilities and data files
libgcrypt20 - LGPL Crypto library - runtime library
libgcrypt20-dbg - LGPL Crypto library - debugger files
libgcrypt20-dev - LGPL Crypto library - development files
libgcrypt20-doc - LGPL Crypto library - documentation
strongswan-plugin-gcrypt - strongSwan plugin for gcrypt

```

May be check your /var/log/boot.log for any error we could work with ?

---

### Post by hl1sxa2 on 2014-08-14
Thanks, [COLOR=#000000]bapoumba [/COLOR]:D[COLOR=#000000] & [/COLOR][COLOR=#000000]scott092707 [/COLOR]:p[COLOR=#000000]

I have a same problem with [/COLOR][COLOR=#000000]scott092707, 'delayed on libgcrypt 1.5.3 at that time'.
And the same contents with [/COLOR][COLOR=#000000]bapoumba. 
(some text are KOREAN)
[/COLOR]> apt-cache search 
libgcryptlibgcrypt11-dbg - LGPL Crypto library - debugger files
libgcrypt11-dev - LGPL Crypto library - development files
libgcrypt11-doc - LGPL Crypto library - documentation
libgcrypt11 - LGPL &#50516;&#54840;&#54868; &#46972;&#51060;&#48652;&#47084;&#47532; - &#47088;&#53440;&#51076; &#46972;&#51060;&#48652;&#47084;&#47532;
libgpg-error-dev - library for common error values and messages in Gnulibgpg-error-dev - library for common error values and messages in GnuPG components (development)
libgpg-error0 - GnuPG &#44396;&#49457;&#50836;&#49548;&#50640;&#49436; &#51068;&#48152; &#50640;&#47084;&#44050;&#44284; &#47700;&#49884;&#51648;&#47484; &#50948;&#54620; &#46972;&#51060;&#48652;&#47084;&#47532;
libcrypt-gcrypt-perl - Perl interface to the GNU Cryptographic librarylibcrypto++-dev - General purpose cryptographic library - C++ development
libcrypto++-doc - General purpose cryptographic library - documentation
libcrypto++-utils - General purpose cryptographic library - utilities and data files
libgcrypt20 - LGPL Crypto library - runtime library
libgcrypt20-dbg - LGPL Crypto library - debugger files
libgcrypt20-dev - LGPL Crypto library - development files
libgcrypt20-doc - LGPL Crypto library - documentation
strongswan-plugin-gcrypt - strongSwan plugin for gcrypt
[COLOR=#000000]
Right?

And, I checked, there's no error or fail message in my [/COLOR][COLOR=#000000]/var/log/boot.log.

Thanks to advance![/COLOR]

---

### Post by s-terenzi on 2014-09-18
happened this thing with [COLOR=#000000] libgcrypt 1.5.3 after i've been messing aound a bit to enable hibernation feature, so tried tuxonice[/COLOR] but wasn't necessary (for 14.04 i enabled hibernation with the procedure explained in the last post of this thread &#8594;[http://askubuntu.com/questions/94754/how-to-enable-hibernation](http://askubuntu.com/questions/94754/how-to-enable-hibernation) ) and so removed it, then noticed the said problem.
Solved removing tuxonice and related packages, plus sudo apt-get autoremove which removed the package "uswsusp"(you can find it through synaptic package manager). When rebooted all was back to normal.
Hope will help.

---

