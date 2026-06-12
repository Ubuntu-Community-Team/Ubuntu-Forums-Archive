---
title: "Uncorking wine"
date: 2005-06-04
forum: General Help
---

### Post by yenruoj on 2005-06-04
If I wish to install wine on a computer that does not have an internet connection, is it possible to download all the *.deb files in [http://wine.sourceforge.net/apt/hoary/](http://wine.sourceforge.net/apt/hoary/), copy these to the destination machine and them simply do a dpkg -i wine*.deb on that box?

Is there a better solution?

Many thanks in advance!

---

### Post by bored2k on 2005-06-04
[QUOTE=yenruoj]If I wish to install wine on a computer that does not have an internet connection, is it possible to download all the *.deb files in [http://wine.sourceforge.net/apt/hoary/](http://wine.sourceforge.net/apt/hoary/), copy these to the destination machine and them simply do a dpkg -i wine*.deb on that box?

Is there a better solution?

Many thanks in advance![/QUOTE]
 It should work.

---

### Post by yenruoj on 2005-06-04
Thanks -- I'll give it a try ...

---

### Post by yenruoj on 2005-06-08
Well, using this method, dpkg works but reports package dependency problems.

Looking at the related packages on packages.ubunto and following the "depends" links, this details further packages that appear to have their own related packages, with "depends" links, etc.

Is there a simple way of downloading all package dependent *.deb files so that they can all be found by dpkg?

---

### Post by shakin on 2005-06-08
[QUOTE=yenruoj]Well, using this method, dpkg works but reports package dependency problems.

Looking at the related packages on packages.ubunto and following the "depends" links, this details further packages that appear to have their own related packages, with "depends" links, etc.

Is there a simple way of downloading all package dependent *.deb files so that they can all be found by dpkg?[/QUOTE]

Do the install on a network-connected computer using apt-get and use the -d option, which will just download the packages and not install them. Then you can grab all those debs from the apt cache, copy them to a CD or whatever else, then install them all on the other computer.

---

### Post by yenruoj on 2005-06-08
Thanks, shakin -- my problem is that my Ubuntu host is not, and cannot be connected to the internet!

---

### Post by Joeb on 2005-06-08
I'm jumping in here, so excuse the interruption.  If I understand you correctly, your Ubuntu computer is not on the internet and you are using some other computer to connect and download the files you need.  If so, and I haven't actually tried this, so it might not even work, but if so, you could boot of the LiveCD on the machine you are using to download and then run the apt-get command that was mentioned.  You may have to create a symlink to an area on the hard drive for that machine, however. 

If that doesn't work, you could, while in the LiveCD run Synaptic and select the Wine package you want to install and then look at the dependencies and manually write them down.

---

### Post by yenruoj on 2005-06-11
Thanks for eveyone's help.

I have not yet tried the LiveCD solution suggestede by Joeb -- I'm not sure if this would detect the necesary modem drivers -- can anyone confirm?

However, I think that I may have downloaded the required packages and so trying:

$ sudo dpkg -i wine_0.0.20050419-winehq-1_i386.deb

gives me:

(Reading database ...
Unpacking wine ...
dpkg-deb: (subprocess): short read in buffer_copy (failed to write pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg:error processing wine_0.0.20050419-winehq-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/wine/d3d8.dll.so')


I'm not quite sure what this means.

Many thanks in anticipation.

---

### Post by Picklegnome on 2005-08-20
I also cannot hook my Ubuntu computer up to the 'net. I downloaded wine, libwine, and wine-utils, and burned the .deb s to a cd. I was able to use dpkg successfully for all of them, and when I looked in the Synaptic Package Manager, wine-utils and wine were there (under "Cross Platform"). What steps do I need to take to be able to open .exe files now? When I try, it says there is nothing to open it with.

Thanks!

---

