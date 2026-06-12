---
title: "Can't find official archive mirror."
date: 2015-02-20
forum: General Help
---

### Post by CantankRus on 2015-02-20
I've used this [**_[COLOR="#B22222"]iinet mirror[/COLOR]_**]("https://launchpad.net/ubuntu/+mirror/ftp.iinet.net.au-archive") 
for a few years now with no problems.
I switched to the main server for a while and now want to switch back but the iinet mirror is no longer in the server list.
[ATTACH=CONFIG]260097[/ATTACH]

Anyone know how I can get it back in the list.
It's listed in the [**_[COLOR="#B22222"]Official Archive Mirrors[/COLOR]_**]("https://launchpad.net/ubuntu/+archivemirrors") on launchpad.
iinet is my ISP so they are unmetered downloads.

This is the list how it looks when logged into a live cd...
[ATTACH=CONFIG]260102[/ATTACH]

---

### Post by v3.xx on 2015-02-20
What about using 'sudo sed'?

Example:
```
sudo sed -i 's/us.archive.ubuntu.com/mirror.math.ucdavis.edu/' /etc/apt/sources.list
```
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+ubuntu+mirror+in+terminal+sudo+sed&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+ubuntu+mirror+in+terminal+sudo+sed&sa=Search&cof=FORID:9)

---

### Post by CantankRus on 2015-02-21
> **v3.xx said:**
> What about using 'sudo sed'?

Example:
```
sudo sed -i 's/us.archive.ubuntu.com/mirror.math.ucdavis.edu/' /etc/apt/sources.list
```
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+ubuntu+mirror+in+terminal+sudo+sed&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+ubuntu+mirror+in+terminal+sudo+sed&sa=Search&cof=FORID:9)

I copied  my /etc/apt/sources.list from my Vivid install where the iinet mirror still shows and replaced the instances of "vivid" with "trusty".

It works but not ideal as the sources are placed in "Other Software" because the iinet mirror is not listed.
[ATTACH=CONFIG]260135[/ATTACH] [ATTACH=CONFIG]260136[/ATTACH]

Would like to know how to get iinet back in the mirror list.

---

### Post by CantankRus on 2015-02-21
**Fixed** ... I found the file that lists the mirrors....
**/usr/share/python-apt/templates/Ubuntu.mirrors**
Just added the iinet mirror and all good. :KS

---

