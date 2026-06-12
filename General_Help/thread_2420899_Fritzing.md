---
title: "Fritzing"
date: 2019-06-12
forum: General Help
---

### Post by johny-pineault-4 on 2019-06-12
Hi !!!

So I just done a fresh install of Ubuntu 18 on my pc and everything work (Steam , kicad ect ) so I checked for Fritzing in the Ubuntu software and it's outdated and the last update on the official site is since 2016 I think. Anyway, so i download the package from the oficial website and extract I try it , got an error from the app that say bin part and data are missing but the gui is there . So I chek around and see that the part folder are empty and there is another folder containing the part so I paste it and try and it dosent work the app didnt lunch. I try the one on Ubuntu Software and I get error in the app too. So I found tutorial online that seem to be okay since it all does what ive done but in the terminal and more thing . 

So know my trouble is that the app didnt lauch at all ( the 9.3 one on official ) if the one on Ubuntu Softare isn't install( 9.2) but when I install the one on the Ubuntu Software both only start the splash screen logo then close
Ive tried delete every thing and do it again but nothing.

there is the tutorial
[https://howto-ubuntunew.blogspot.com/2016/08/install-fritzing-093b-electronic.html](https://howto-ubuntunew.blogspot.com/2016/08/install-fritzing-093b-electronic.html)

---

### Post by Xian on 2019-06-12
You say that you're running Ubuntu 18.04 and want to install fritzing version 0.9.3b  ..... correct?

Isn't the official Ubuntu package already at that version? 
[https://packages.ubuntu.com/bionic/fritzing](https://packages.ubuntu.com/bionic/fritzing)

There is also the option of installing via flathub: [https://flathub.org/apps/details/org.fritzing.Fritzing](https://flathub.org/apps/details/org.fritzing.Fritzing)

---

### Post by johny-pineault-4 on 2019-06-12
yess sorry forgot 0. before 9.3 and the b :sad:

---

### Post by johny-pineault-4 on 2019-06-12
so i'm sticking on that problem and don't know what to do :/

---

### Post by QIII on 2019-06-12
Have you tried 
```
sudo apt install fritzing
```
?

0.9.3b is in the repo.

---

### Post by johny-pineault-4 on 2019-06-13
When is in the repo will I see it in the software browser (the Ubuntu "app store ")
Just done that and it seam to have insalled the 0.9.3b and I only get the fritzing splash screen and then nothing

---

### Post by johny-pineault-4 on 2019-06-13
I don't get any error only the boot logo then it disapear

---

### Post by johny-pineault-4 on 2019-06-14
i've tried to delete file in the .config folder and then the one in documents and re instal it with the instruction in the link i've put over and still nothing.

---

### Post by again? on 2019-06-14
Try installing fritzing-parts as well.
```
sudo apt install fritzing fritzing-parts
```

Then via terminal run (note the capitalized "F". This command sets the parts directory to /usr/share/fritzing/parts)....
```
Fritzing
```

If errors post the output of...
```
apt policy fritzing*
```

eg my output on 18.04 where fritzing starts....
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt policy fritzing***
fritzing:
  Installed: 0.9.3b+dfsg-4.1ubuntu1
  Candidate: 0.9.3b+dfsg-4.1ubuntu1
  Version table:
 *** 0.9.3b+dfsg-4.1ubuntu1 500
        500 http://ftp.iinet.net.au/pub/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
fritzing-parts:
  Installed: 0.9.3b-1
  Candidate: 0.9.3b-1
  Version table:
 *** 0.9.3b-1 500
        500 http://ftp.iinet.net.au/pub/ubuntu bionic/universe amd64 Packages
        500 http://ftp.iinet.net.au/pub/ubuntu bionic/universe i386 Packages
        100 /var/lib/dpkg/status
fritzing-data:
  Installed: 0.9.3b+dfsg-4.1ubuntu1
  Candidate: 0.9.3b+dfsg-4.1ubuntu1
  Version table:
 *** 0.9.3b+dfsg-4.1ubuntu1 500
        500 http://ftp.iinet.net.au/pub/ubuntu bionic/universe amd64 Packages
        500 http://ftp.iinet.net.au/pub/ubuntu bionic/universe i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by johny-pineault-4 on 2019-06-14
that make it , i was adding the part manualy with the one downloaded on the oficial website :|:|:|=d>
Thanks you and I learn a new command too ( been a long time since I used linux ) 
By the way do you have any recomendation for simulation software like Proteus ect. 
And if you have good thing too for engenering desing

---

### Post by again? on 2019-06-14
> **johny-pineault-4 said:**
> that make it , i was adding the part manualy with the one downloaded on the oficial website :|:|:|=d>
Thanks you and I learn a new command too ( been a long time since I used linux ) 
By the way do you have any recomendation for simulation software like Proteus ect. 
And if you have good thing too for engenering desing
No recommendations....not my field...just tested the application.

---

### Post by johny-pineault-4 on 2019-06-14
Thanks again , one question : why when you do sudo app install it instal the lastest version but in the ubuntu software it dosen't ?

---

### Post by again? on 2019-06-15
> **johny-pineault-4 said:**
> Thanks again , one question : why when you do sudo app install it instal the lastest version but in the ubuntu software it dosen't ?
Referring to fritzing I don't see different versions.
[ATTACH=CONFIG]283437[/ATTACH]

Some packages may show different versions if it is has a [**snap package**]("https://itsfoss.com/use-snap-packages-ubuntu-16-04/"). <---link
For instance if you search vlc in Ubuntu Software you'll find 2 occurrences.
A snap package and a regular compiled package.  (Source line in pics)
[ATTACH=CONFIG]283432[/ATTACH] [ATTACH=CONFIG]283433[/ATTACH]

Apt does not show or install snap packages.
eg spotify is only available as a snap.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt install spotify**
[sudo] password for glen:         
Reading package lists... Done
Building dependency tree       
Reading state information... Done

No apt package "spotify", but there is a snap with that name.
Try "snap install spotify"

E: Unable to locate package spotify

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo snap install spotify**
Download snap "spotify" (35) from channel "stable"
1.1.5.153.gf614956d-16 from Spotify&#10003; installed

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt policy spotify**
N: Unable to locate package spotify

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] snap list**
Name               Version                     Rev   Tracking  Publisher   Notes
core               16-2.39                     6964  stable    canonical&#10003;  core
core18             20190508                    970   stable    canonical&#10003;  base
gnome-3-28-1804    3.28.0-10-gaa70833.aa70833  55    stable    canonical&#10003;
gtk-common-themes  0.1-16-g2287c87             1198  stable    canonical&#10003;
snap-store         20190613.4078f5b            136   stable    canonical&#10003;
spotify            1.1.5.153.gf614956d-16      35    stable    spotify&#10003;
```
[ATTACH=CONFIG]283436[/ATTACH]



Note snap packages are much larger than regular packages as they contain dependencies.

---

### Post by johny-pineault-4 on 2019-06-15
Interesting.

 In the store I only see the 0.9.2

---

