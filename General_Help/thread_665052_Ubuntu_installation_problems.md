---
title: "Ubuntu installation problems"
date: 2008-01-11
forum: General Help
---

### Post by whaevr on 2008-01-11
I'm at wits end here...

HP Pavilion
Pentium 4 CPU 3.00GHz
1GB of RAM
NVidia GeForce 6200...

I've been trying to install Ubuntu for two days now, almost three.

I started out by trying to download Ubuntu 7.10 from the website, then I burned it to a CD and restarted comp.

When I select "Start or Install" or "Safe graphics mode" the loading bar appears, goes from side to side for a bit then the whole thing gets distorted and the loading bar splits into 3 across the screen, and everything looks kinda pixalated...I let it sit there and nothing happened so I assumed I burnt the CD wrong.

Looked up a tutorial, no I burnt it right...tried it again same thing. I downloaded 7.10 from another source, same thing. I did an MD5 check on both of them, they both turn out correct.

So then I hear about this program called Wubi. I download it, it downloads Ubuntu 7.04 and installs it. At this point I think I did it...nope. when I select Ubuntu from the boot screen it loads for a bit...then the bar just stops. Doesn't move, I let it sit there for a while and the bar doesn't gain any more progress.

I tried using the alpha release of Wubi 7.10, it just tried to load Ubuntu like it was on a live CD and I run into the messed up loading bar I described earlier.

So now I'm pretty much lost...

*Note* I would rather install 7.10 instead of 7.04...

Please help. :(

---

### Post by fazavon on 2008-01-11
The issue is that 7.10 is not seeing your video card as is, you should try the alt install 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

make sure you check the box that reads "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer." 

Then when you have it installed you should have some crazy screen res, 800X600 or something close. You can then install the restricted drivers for your video card.

Let me know if you have any questions.

thanks

//j

---

### Post by whaevr on 2008-01-11
Alright...hopefully that will do it...oh boy I get to download it...AGAIN >.<

---

### Post by jimrz on 2008-01-11
try downloading the "alternate" install cd. the text based  installer is quite straightforward and easy to follow + seems not to encounter some of the problems that the gui installer on the "live" cd does with some equipment.

---

### Post by whaevr on 2008-01-12
I went to the download site, checked the box but when I downloaded and burnt to a CD. It looked exactly like the Live CD...there was no text installation and it froze again at the loading bar like in my first post...should I try to redownload the text based install?

Edit:
Should it have been named differently if I checked the box? It was named the same as my Live CD version...

---

### Post by kristian64 on 2008-01-12
it seems to me that checking that box does nothing, but when you get to the download page there is a link to file, for example:
```
http://ftp.estpak.ee/pub/ubuntu-releases/gutsy/ubuntu-7.10-desktop-amd64.iso
```
I changed desktop to alternate and got the right file (I think) so the link was
```
http://ftp.estpak.ee/pub/ubuntu-releases/gutsy/ubuntu-7.10-**alternate**-amd64.iso
```

Install still failed during the installation of the base system. I did md5 check and checked CD itegrety and got no problems. Any ideas?
edit: never mind, found the answer to my problem in another topic

---

