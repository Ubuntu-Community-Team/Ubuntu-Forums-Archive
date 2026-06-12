---
title: "[SOLVED] Need to downgrade to TrueCrypt 4.3a from 5.0"
date: 2008-02-07
forum: General Help
---

### Post by tmastran on 2008-02-07
I "upgraded" to TrueCrypt 5.0 and discovered that hidden volume support is poor. I can mount and read existing volumes, but copying large (100 MB +) files to them stalls and eventually brings my system to a halt, requiring a hard reboot.

I don't have a backup of the 4.3a deb, and can not find it on the TrueCrypt web site. Does anyone have a link to where I can download it? Thanks!

In my opinion there are serous changes in 5.0  that are not documented in the release notes. Beware.

System:

Ubuntu 7.10
Linux 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux

---

### Post by apetresc on 2008-02-07
There's still a 4.3a deb here: [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/truecrypt_4.3a-0_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/truecrypt_4.3a-0_i386.deb)

Enjoy :)

---

### Post by tmastran on 2008-02-07
Thank you!

---

### Post by mveltre on 2008-02-07
I got almost the same problem but with a "fresh" formatted truecrypt volume (whirlpool, aes). After moving about 80mb to the disk, the system load goes up until it freezes...

---

### Post by tmastran on 2008-02-07
I only had problems with a previously created hidden volume. I created a "fresh" normal volume and copied a couple hundred meg to it with no problems. Mine also crapped out at around 80 meg. I'm running KDE also if that makes any difference.

---

### Post by jbkerns on 2008-02-08
Does anyone have the Truecrypt 4.3a AMD64 Gutsy deb?  Something tells me that I am going to hate 5.0 and want the safety net of having a restore deb in my pocket.

[Edit]  Is the 32 bit .deb posted above for Gutsy as well?

[Another Edit]  I discovered that torrents still exist for 4.3a.  Lession learned:  if I install something off package manager, save the debs!  I hate being a noob.

Thanks in advance.

---

### Post by Henrik.Schack on 2008-02-09
I got the same problem after moving 80-85 MB to a truecrypt volume, my system locks up.
New or old volume format makes no difference.

---

### Post by MountainX on 2008-02-11
> **jbkerns said:**
> 
[Another Edit]  I discovered that torrents still exist for 4.3a. 

How do I get TrueCrypt 4.3a (amd64) via bittorrent? I'm new to Linux -- haven't used the BitTorrent software yet.

---

### Post by jbkerns on 2008-02-11
I tried to use TC5 but it was... um.... problematic.

I did a search on thepiratebay.org for the torrent and got it.  The source, 32bit and 64 bit debs were there, along with the Windows version.  

Recently both of my Ubuntus (32 and 64) had a kernel system upgrade and the 32 bit deb would not install.  Like yourself I am a noob and although I followed some older posts about the kernel module issues, I could not get the source to compile. I decided not not post the problems on the forums, but go another way. I did not want to invest the time in getting 4.3a back if it was going to die or become uninstallable again at the next kernel update.

I spend the weekend converting my truecrypt volumes using the Windows client into 7z archives encrypted with GPG. Good faithful old GNU...

After I am positive that I got all my TC volumes converted, I will uninstall truecrypt and hope that they will re-instate the lost linux functionality in 6.0. I loved Truecrypt, and still want to "come back home."  This is a very important project needed for these troubled times.

Respectfully....

[Added 13FEB] I have been experimenting with Encrypted Loopback devices and on the Ubuntu side, I have had very good performance with loop-aes.  I am looking forward to playing more with this and other schemes.  I also plan to use FreeOTFE on the Windows side in order to get the cross platform compatiability back.

---

### Post by MountainX on 2008-02-11
Sorry to hear about your TrueCrypt problems. Let's hope they will address the current TC 5.0 issues well before version 6.0.

Thanks for the link to thepiratebay.org. Unfortunately, the Linux versions of TC do not appear to be there any longer... and now that you have explained the problems with kernel updates and 4.3a, I also find myself in a dilemma.

I wonder if TC 5.0 for WIndows is working well? Maybe I'll use that.

---

