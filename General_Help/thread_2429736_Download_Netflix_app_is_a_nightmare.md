---
title: "Download Netflix app is a nightmare"
date: 2019-10-22
forum: General Help
---

### Post by lukytachic on 2019-10-22
I am getting this errors all the time, I have checked many websites trying different ways of solving this problem but it looks like it is impossible. I am sorry I am also not a pro at computers not like others that seem to control the linux program.

When I type on the terminal- sudo apt-add-repository ppa:ehoover/compholio I get this:

Err:17 [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) bionic Release      
  404  Not Found [IP: 91.189.95.83 80]
Err:18 [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) bionic Release      
  404  Not Found [IP: 91.189.95.83 80]
Err:19 [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Err:5 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease
  Las firmas siguientes no se pudieron verificar porque su clave pública no está disponible: NO_PUBKEY 76F1A20FF987672F    ( IT SAYS: The signatures couldn't be verified because the public key isn't avaliable)
Err:7 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease
  Las firmas siguientes no se pudieron verificar porque su clave pública no está disponible: NO_PUBKEY 4773BD5E130D1D45


Thanks a lot for your help

---

### Post by deadflowr on 2019-10-22
[I]Thread moved to **General Help**
[/I]

No longer needed.
Netflix works out of the box on Google Chrome and Firefox on Linux.

Also these PPAs are no longer available, so run
```
sudo apt-add-repository -r ppa:ehoover/compholio 
sudo add-apt-repository -r ppa:pipelight/stable
sudo add-apt-repository -r ppa:gwibber-daily/ppa
sudo apt update
```
to remove them.

You have other issues with winehq and spotify repos, but I'm not sure what needs to be done there...
For the moment.

---

### Post by lukytachic on 2019-10-23
Thanks a lot, but does it work like in the app? I mean can I download a film and see it later? And if it is like this how do I do it?

---

### Post by deadflowr on 2019-10-23
> **lukytachic said:**
> Thanks a lot, but does it work like in the app? I mean can I download a film and see it later? And if it is like this how do I do it?

As far as I know downloading on Linux isn't supported.
But the ability to do so was never supported by those PPAs either.

Netflix on Linux is strictly through a browser.

---

### Post by hk42 on 2019-10-23
Hi
I managed to download and install the Netflix add-on for Kodi.
It works well and the user interface is interesting.
My account is SD only though.

---

### Post by lukytachic on 2019-10-24
But for that I need to pay a VPN, am I right?

---

### Post by hk42 on 2019-10-26
No I don't use a VPN just my basic 8&#8364;/month Netflix subscription.
Setting of Kodi is rather complicated and you have to search the Web for the 
Netflix addon.
It doesn't support downloading only my Android phone does that.
Worth a try IMHO.
PS: It seems that the Kodi version proposed by Ubuntu is not the last one and 
The Netflix add-on is not compatible.
The good version is 18.4 and on the Kodi site there is a nice tutorial for
installation on Ubuntu.

---

