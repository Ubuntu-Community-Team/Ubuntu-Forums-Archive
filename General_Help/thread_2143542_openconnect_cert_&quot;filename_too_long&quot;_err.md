---
title: "openconnect cert &quot;filename too long&quot; error"
date: 2013-05-09
forum: General Help
---

### Post by jbeiter on 2013-05-09
Ok I'm perplexed on this. I'm getting an error running openconnect, calling a cert that is pulled from a smart card on a system running 12.04. I installed the same packages on another laptop running 13.04, upgraded from 12.04. It runs fine. The scripts are identical.

Others in my group are running this just fine as well. The cert string was pulled off of the smart card. I can't figure out why this system is throwing an error on the file name string.

Any idea why I would be getting this error?

root@atom:~/bin# cat vpn.sh
sudo openconnect -c 'pkcs11:library-description=Smart%20card%20PKCS%2311%20API;library-manufacturer=OpenSC%20%28www.opensc-project.org%29;model=PKCS%2315%20emulated;manufacturer=piv_II;serial=06b519820810d7ff;token=PIV_II%20%28PIV%20Card%20Holder%20pin%29;id=%01;object=PIV%20AUTH%20key' --authgroup=myauthgroup [https://mycompanyvpn.com](https://mycompanyvpn.com)

root@atom:~/bin# ./vpn.sh
Attempting to connect to 169.111.111.111:443
Failed to open certificate file pkcs11:library-description=Smart%20card%20PKCS%2311%20API;library-manufacturer=OpenSC%20%28www.opensc-project.org%29;model=PKCS%2315%20emulated;manufacturer=piv_II;serial=06b519820810d7ff;token=PIV_II%20%28PIV%20Card%20Holder%20pin%29;id=%01;object=PIV%20AUTH%20key: File name too long
Loading certificate failed. Aborting.

I tried using double quotes instead of single.. that didn't help though. I tried removing sections of the cert string but only get a "file not found" at some point.

(note: I masked my IP, vpn server, etc...)

---

### Post by dwmw2 on 2013-05-09
Please see the "Getting Help" section at [http://www.infradead.org/openconnect/mail.html](http://www.infradead.org/openconnect/mail.html)

I suspect your non-working version of OpenConnect is built without PKCS#11 support so it's trying to treat that whole PKCS#11 URL as a filename... which is, as it tells you, too large.

Run '[FONT=courier new]openconnect --version[/FONT]' and compare between the two, to confirm.

---

### Post by jbeiter on 2013-05-09
This looks like the problem.. the working system (ubuntu 13.04) is:

 openconnect --version
OpenConnect version v4.07
Using GnuTLS. Features present: PKCS#11, DTLS (using OpenSSL)


broken one (ubuntu 12.04)
 openconnect --version
OpenConnect version v3.15

can't seem to find a way to install 4.07 on this box short of chasing down source and dependancies. Its like being on freebsd again!

---

