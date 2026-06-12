---
title: "installing Privit Internet Accsess on Odroid"
date: 2017-02-27
forum: General Help
---

### Post by orbitmipi on 2017-02-27
Helow all 

I'm new hear. Moderintly noob to linux. But I tryd finding help on this with the tec suport. Not much luck. I also went to the Odroid forum and thear seems to be inactive.

 I have tryed the PIA websites tutorial.Ween I try to instal the zip for the gui app version I cant get past :
./pia-v68-installer-linux.sh
I get thess error's:
./installer_linux/32/ruby/: 1: ./installer_linux/32/ruby: Syntax error: Unterminated quoted string

Ween I try the other option of instaling openvpn wen I typ "ls -l"  I get:
-rw-r--r-- 1 root root 2719 Feb 26 02:11 pia-ca.rsa.4096.crt
-rwxr-xr-x 1 root root 1381 Feb  2 20016 update-resolv-conf

---

### Post by QIII on 2017-02-27
Hello and welcome to the Forums!

Would you please include a link to the tutorial you are using?

What is it you are trying to accomplish as your ultimate goal?

Thanks.

---

### Post by orbitmipi on 2017-02-27
[https://www.privateinternetaccess.com/installer/download_installer_linux](https://www.privateinternetaccess.com/installer/download_installer_linux)
I trying to get pia and run the odroid ux4 as a media player/torrent box.

---

### Post by QIII on 2017-02-27
Is this software ported to ARM so that your XU4 can run it?

---

### Post by orbitmipi on 2017-02-27
most likly the PIA gui app is not ported for ARM. 
On my pi zero I had no problem using terminal and openvpn but I cant remimber what I did to get PIA on it. I thaink I had to cross use multipul tutorials to get it working .
Is it posabul the apt-get on ubuntu-mate 16.4 gave me the rong openvpn ? I got ubuntu-mate 16.4 from the odroid websit/forum so it shuld be corect.

---

### Post by orbitmipi on 2017-02-27
OMG well I gusse I tryed unziping openvpn from desktop and it did not work becaus I redid it from terminal and now I can see all the vpn ip servers.

If any 1 ever see's this and knows of a way to have desktop PIA app on ARM let me know. Mainly becaus the openvpn option does not have a kill switch if VPN disconects or fails.

---

### Post by orbitmipi on 2017-02-27
> **QIII said:**
> Is this software ported to ARM so that your XU4 can run it?

TY for your time and help

---

