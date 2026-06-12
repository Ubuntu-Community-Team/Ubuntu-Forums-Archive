---
title: "[Ubuntu 12.10] Problem with installation of Sopcast."
date: 2012-10-18
forum: General Help
---

### Post by Kajoo on 2012-10-18
Hi. I have been trying to install Sopcast on new Ubuntu 12.10. I added ppa to my repository, later I updated it and I typed in the command to install sopcast and I get this in return:

> carlo@CarloPC:~$ sudo apt-get install sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 sopcast-player : Depends: sp-auth (>= 3.0.1) but it is not installable
E: Unable to correct problems, you have held broken packages.


---

### Post by Kajoo on 2012-10-19
Anyone?

---

### Post by Kajoo on 2012-10-20
I solved the problem. All I had to do was download and install sp-auth_3.2.6.1~lffl~natty~ppa_i386.deb. It's available to download from Launchpad website. [https://launchpad.net/~ferramroberto/+archive/sopcast/+build/2405344](https://launchpad.net/~ferramroberto/+archive/sopcast/+build/2405344)

---

### Post by Mogen317 on 2012-10-28
Didn't work for me because my ubuntu is 64bit.

Anyone know where I can find a 64bit deb package of sp-auth?

---

### Post by Pilot6 on 2012-10-28
It is in the same repository both 64 and 32 bit
[https://launchpad.net/~ferramroberto/+archive/sopcast/+files/sp-auth_3.2.6~ppa~precise~lffl_amd64.deb](https://launchpad.net/~ferramroberto/+archive/sopcast/+files/sp-auth_3.2.6~ppa~precise~lffl_amd64.deb)

---

### Post by fonsi2099 on 2012-10-29
thanky Pilot6 that worked for me!!
Quote: Pilot6 	
Re: [Ubuntu 12.10] Problem with installation of Sopcast.
It is in the same repository both 64 and 32 bit
[https://launchpad.net/~ferramroberto...lffl_amd64.deb](https://launchpad.net/~ferramroberto...lffl_amd64.deb)
End quote.

If not installed, copy and paste:
[https://launchpad.net/~ferramroberto...lffl_amd64.deb](https://launchpad.net/~ferramroberto...lffl_amd64.deb)
and:
sudo add-apt-repository ppa:ferramroberto/sopcast
sudo add-apt update
sudo apt-get update && sudo apt-get install sopcast-player

enjoy it

to use VLC player as external player:  got to Preferences/player/** Media Player** (active) Use external player and write in commande: vlc
close
That's all.

:guitar:

---

### Post by rainbatt on 2012-11-03
That helps, thanks..

---

