---
title: "Beagle with Webservices in Ubuntu"
date: 2005-10-04
forum: General Help
---

### Post by jwilsie on 2005-10-04
I have been attempting to setup a beagle web-enabled server for the purpose of hosting a large number of documents that need to be searched.  Does anyone here know if a package exists for Ubuntu that might be able to install a copy of Beagle with Webservices enabled.  I have Beagle working fine per the instructions on the Beagle website, but their instructions for the Web-enabled version ask to build the software from source, I am close to being able to do this, but have hit a bit of a snag.  When doing the ./configure i get this error:

checking for gtk-sharp-2.0 glade-sharp-2.0 gecko-sharp-2.0 gnome-sharp-2.0 gconf-sharp-2.0 gmime-sharp >= 2.1.16... Requested 'gmime-sharp >= 2.1.16' but version of gmime-sharp is 2.1.13

configure: error: Library requirements (gtk-sharp-2.0 glade-sharp-2.0 gecko-sharp-2.0 gnome-sharp-2.0 gconf-sharp-2.0 gmime-sharp >= 2.1.16) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I have tried to adjust the "PKG_CONFIG_PATH" per the beagle installation guile on their website, and have even used apt-get to install the only package that sounds like one of the ones in that list, sharp2.  I have worked through several other dependencies already and this is getting to be a pain.  If someone knows of a prebuilt package with the web-enabled switch on, or how to get past that particular problem, I'd appreciate it very much.
Thanks
jwilsie

---

### Post by jwilsie on 2005-10-04
I also made sure that there was no "gmime-sharp" available through apt-get at this time, I am not sure if there is another package they are talking about that I should use.

---

