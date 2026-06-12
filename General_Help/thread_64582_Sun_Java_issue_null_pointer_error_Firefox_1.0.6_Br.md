---
title: "Sun Java issue null pointer error Firefox 1.0.6 Browser"
date: 2005-09-11
forum: General Help
---

### Post by primeaudio on 2005-09-11
I'm new here hope I'm posting this in the right place,
 
Ok  having an issue with Sun Java here are the steps I've taken after a clean install of Ubuntu Hoary and after applying latest updates and changing my Kernel to AMD-K7 in synaptic from the i386 default.

First thing I did was about:config  changed the network IDN to false because of that new security issue..............

I then downloaded Jre update 4 at the sun websight and updated my  apt 
source list with:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted multiverse

next I did apt-get update  then I downloaded  javapackage fakeroot and 
gcc 

Ok  In my user account after the new java file was created:

fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin

Ok then I logged into  root and did: dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb

logged out then logged back in and did

java -version 

Then I surfed over to [http://www.chesslive.de/](http://www.chesslive.de/)  to see if I could load a chess web 
database but whenever I do  that I keep getting a java.lang pointer Exception error:( and  sometimes firefox hangs I've tried different sights but same thing.

The previous time I installed java it worked perfectly on the first shot this
only happened yesterday.

---

