---
title: "64 bit Adobe Flash Player"
date: 2008-04-09
forum: General Help
---

### Post by satimis on 2008-04-09
Hi folks,


Ubuntu 7.04 server amd64
Mozilla Firefox


Please advise where can I download 64bit Adobe Flash Player.  Is it available on repo?


I can't find the package on;
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)


TIA


B.R.
satimis

---

### Post by chrisccoulson on 2008-04-09
There is no 64-bit Flash Player plugin available. However, the 32-bit plugin works in 64-bit Firefox using the nspluginwrapper. If you're running 7.10, then installing flashplugin-nonfree from the repositories should automatically install and set up nspluginwrapper for you.

---

### Post by satimis on 2008-04-09
> **chrisccoulson said:**
> There is no 64-bit Flash Player plugin available. However, the 32-bit plugin works in 64-bit Firefox using the nspluginwrapper. If you're running 7.10, then installing flashplugin-nonfree from the repositories should automatically install and set up nspluginwrapper for you.
Thanks for your advice.


I can't find the package on;
[https://addons.mozilla.org/](https://addons.mozilla.org/)


I found it on Adobe website.  Could you please point me its URL.  TIA


Furthermore can 32bit Adobe Reader addon work on 64 bit Firefox?  I'm running Ubuntu 7.04 server amd64.


B.R.
satimis

---

### Post by kpkeerthi on 2008-04-09
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Flash_9_on_64_bits_system_.28x86_64.29](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Flash_9_on_64_bits_system_.28x86_64.29)

---

### Post by kpkeerthi on 2008-04-09
[http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html)

---

### Post by satimis on 2008-04-09
> **kpkeerthi said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Flash_9_on_64_bits_system_.28x86_64.29](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Flash_9_on_64_bits_system_.28x86_64.29)
Thanks for your URL


$ sudo apt-get install flashplugin-nonfree```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

```


$ apt-cache search flashplugin-nonfree
No printout


$ apt-cache search nspluginwrapper```

nspluginwrapper - A compatibility layer for Netscape 4 plugins

```


Any advice.  TIA


B.R.
satimis

---

### Post by satimis on 2008-04-09
> **kpkeerthi said:**
> [http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html)
$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -```

OK

```


$ sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list```

--00:24:33--  http://www.medibuntu.org/sources.list.d/gutsy.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving www.medibuntu.org... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

100%[=================================================>] 223           --.--K/s             

00:24:34 (6.08 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [223/223]

```


$ sudo apt-get update```

...
....
Reading package lists... Done

```


$ sudo apt-get install acroread mozilla-acroread acroread-plugins```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-acroread has no installation candidate

```
Any advice?  TIA


B.R.
satimis

---

### Post by chrisccoulson on 2008-04-09
For the Flash plugin, you need to enable Multiverse in your sources.list, then
```
sudo apt-get flashplugin-nonfree
```
should do it all for you.

I think it is also possible to run the acroread plugin inside nspluginwrapper for 64-bit Firefox, but AFAIK, Medibuntu doesn't provide a way of doing this from their repository. There is no mozilla-acroread package from Medibuntu for x86-64 systems (only i386). The guide you followed will only work on 32-bit systems.

---

### Post by satimis on 2008-04-09
> **chrisccoulson said:**
> For the Flash plugin, you need to enable Multiverse in your sources.list, then
```
sudo apt-get flashplugin-nonfree
```
should do it all for you.

Have following multiverse repo enabled```

deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```


Following repo are commented out```

# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

```
They are backports repo maybe NOT tested.  Would there is any problem on enabling them?


> 
I think it is also possible to run the acroread plugin inside nspluginwrapper for 64-bit Firefox, but AFAIK, Medibuntu doesn't provide a way of doing this from their repository. There is no mozilla-acroread package from Medibuntu for x86-64 systems (only i386). The guide you followed will only work on 32-bit systems.
Thanks.  I would run xpdf instead.


B.R.
satimis

---

### Post by Cope57 on 2008-04-09
[** Re: About 64bit Adobe Flash Player **]("http://www.linuxforum.com/forums/index.php/topic,186457.msg785910.html#msg785910")
This is fun posting all over for the same thing...

---

