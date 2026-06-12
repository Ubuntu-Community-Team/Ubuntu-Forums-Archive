---
title: "Ubuntu Gnome 13.04 help please"
date: 2013-05-15
forum: General Help
---

### Post by FishboyFive on 2013-05-15
hi everyone i have ubuntugnome 13.04 installed and followed the directions below to upgrade to gnome 3.8 i seems to work but the ubuntu software center crashes each time i try to open it . 

[COLOR=#ff0000]**Directions i followed**[/COLOR] 
[COLOR=#4b0082]For those excited about the latest version of GNOME, we do maintain the [/COLOR][[COLOR=#4b0082]GNOME3 PPA[/COLOR]]("https://launchpad.net/%7Egnome3-team/+archive/gnome3")[COLOR=#4b0082]  to catch an early look at GNOME 3.8. Please ensure you do a  dist-upgrade if you choose to add this PPA and not just a standard  upgrade or GDM and GNOME shell will not run after start-up. As always,  if you choose to make use of any PPA, please familiarize yourself with [/COLOR][[COLOR=#4b0082]ppa-purge[/COLOR]]("http://manpages.ubuntu.com/manpages/raring/man1/ppa-purge.1.html")[COLOR=#4b0082].[/COLOR]

[COLOR=#008000]=== Ubuntu 13.04 (Raring) ===[/COLOR]

[COLOR=#a52a2a]GNOME 3.8 that won't make it into the normal Ubuntu 13.04 repositories. Other parts of GNOME 3.8 are available in the [/COLOR][[COLOR=#a52a2a]https://launchpad.net/~gnome3-team/+archive/gnome3-staging[/COLOR]]("https://launchpad.net/%7Egnome3-team/+archive/gnome3-staging")[COLOR=#a52a2a] PPA but beware that many of those components have known regressions from their GNOME 3.6 versions.
[/COLOR]
[COLOR=#a52a2a] [/COLOR][COLOR=#a52a2a]You need to run 'sudo apt-get dist-upgrade' to avoid problems. Please  read the output before entering 'Y' to make sure important packages  won't be removed.[/COLOR]



any idea why its doing that ?

---

### Post by Frogs Hair on 2013-05-15
PPA's are bleeding edge in many cases and always use at your own risk. I located a bug report that you may want to confirm and if the synaptic package manager is available in 3.8 you can use it to install software until you get the problem sorted out. I have tried 3.8 twice and am back on 3.6.   ```
sudo apt-get install synaptic 
```  

[https://bugs.launchpad.net/software-center/+bug/1178357](https://bugs.launchpad.net/software-center/+bug/1178357)

---

### Post by mayagrafix on 2013-05-16
Or you can go Ubuntu-GNOME distro... it runs 3.8 

[http://ubuntugnome.org/]](http://ubuntugnome.org/])

---

### Post by markbl on 2013-05-16
> **FishboyFive said:**
> hi everyone i have ubuntugnome 13.04 installed and followed the directions below to upgrade to gnome 3.8 i seems to work but the ubuntu software center crashes each time i try to open it .

Has for me also since I added the GNOME 3 PPA. I note it crashes on both Ubuntu GNOME 13.04, and on Ubuntu 13.04 + GNOME Shell. I just use Synaptic or aptitude.

There are a few little problems around after you add the GNOME 3 PPA, this is just one of them. I think GNOME Shell 3.8 is quite a bit better than 3.6 so I live with the problems.

---

### Post by timgood on 2013-05-17
> **mayagrafix said:**
> Or you can go Ubuntu-GNOME distro... it runs 3.8 

[http://ubuntugnome.org/]](http://ubuntugnome.org/])
 
No it doesn't. It comes with 3.6 and you have to manually install 3.8 which is causing the problem.

---

### Post by FishboyFive on 2013-05-17
That is correct . The ubuntugnome.org site says we can update to gnome 3.8 it just did not say anything about software center being borked. I guess I will just wait until next version . After I tried fedora 19 alpha I can't run anything older then gnome 3.8 . Gnome 3.9 in fedora 19 is AMAZING. I love it

---

