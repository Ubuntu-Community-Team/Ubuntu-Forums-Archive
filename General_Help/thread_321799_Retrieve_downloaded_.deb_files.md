---
title: "Retrieve downloaded .deb files"
date: 2006-12-19
forum: General Help
---

### Post by Asix on 2006-12-19
Heya everyone,
I've installed Kubuntu 6.06 a long time ago, and one month ago I completely moved to Linux and started using this distribution. But the suddenly I messed up something and needed to reformat the whole hard drive. Although I saved all my personal documents, I was unable to save any .deb package I downloaded through Adept (or by using apt-get utility), so I needed to download about 50 MB data again, and I am using a slow 64 kbit/s connection to the Internet. 
So my question is: is there a way to retrieve .deb packages downloaded through those utilities, so I can backup them, too, in order to save some bandwidth, because no matter how careful I am, sometimes you just need to wipe out the whole hard drive and start from scratch. Does anyone know the location where Adept and/or apt-get utility store the .deb packages they download, or they delete them after the install? 
Thanks in advance.

---

### Post by christhemonkey on 2006-12-19
All downloaded .deb files are saved to /var/cache/apt/archives/, so you could just back up this directory like this:
```
sudo cp /var/cache/apt/archives/*.deb ~/ 
```

(obviously that would just place them all slap bang in your hom folder an you probably wouldnt want them there!)

---

### Post by earobinson on 2006-12-19
also if you look at your sources.list file (/etc/sources.list) it will tell you the locations ubuntu is downloading packages from!

---

### Post by Asix on 2006-12-19
Yeah I knew that because I'm familiar with sources.list file and all that stuff.
But in that directory there's about 100 MB of .deb packages, so I've backed them all up and then I'll write them to a blank CD, just in case that I need to reformat the hard drive.
Another question:
If I reformat a hard drive and reinstall Kubuntu 6.06 from LiveCD, and then copy all of those .deb packages I backed up earlier and place them in one folder, say /home/<username>/deb_temp and then navigate to that folder through console and run ```
sudo dpkg -i *.deb
``` would that install all packages in that directory without bothering me about package dependencies or something?

---

### Post by christhemonkey on 2006-12-19
>  would that install all packages in that directory without bothering me about package dependencies or something?

Yes.

As long as all dependencies are there!
But they should be if you have not deleted random files or downloaded individual .deb files to random places.

---

### Post by koenn on 2006-12-19
> **christhemonkey said:**
> Yes.

As long as all dependencies are there!
But they should be if you have not deleted random files or downloaded individual .deb files to random places.
I'm not so sure about this. 
If I'm not mistaking, dpkg just installs, but does not handle dependencies. If e dependency is not satisfied, dpkg will complain that it can not install the package. it is apt that handles the dependencies. 

Installing with dpkg would work if you work out an order to the packages so you install first those packages that the others depend on. 

Or you can use apt 'locally'  (from a directory on your computer in stead of an archives server) as explained here:
[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

---

### Post by christhemonkey on 2006-12-19
Dpkg is intelligent too, if you have all debs and all dependencies in the same place, it will install them all in the correct order so as not to give errors.

---

