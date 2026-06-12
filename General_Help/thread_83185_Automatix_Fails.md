---
title: "Automatix Fails"
date: 2005-10-28
forum: General Help
---

### Post by UzbrojonyBandyta on 2005-10-28
I have installed 5.10 from scratch. First thing I did after that was downloading automatix 2.13 from this forum and launching it. Following instructions I did not install prelink. And what i got ??? 
1. Even if Automatix says everything was installed, NOTHING has been really installed. I still dont have nor mplayer nor codecs nor ANY other software from the list. 
2. Synaptic says that there are broken packeges with gstreamer-plugins and opera. apt-get -f install says the problem is that gstreamer-visual wants to overite something from gstreamer-misc. apt-get -f install  fails and nothing is repaired !
3. When doing apt-get update I get 

 W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: You may want to run apt-get update to correct these problems

What is going on ? I am doing the same installation from scratch for the third time and still those problems ! It seems that there is somthing really wrong with Automatics scripts.

Please, help me. Do I do anything wrong ?

---

### Post by z_pod on 2005-10-28
Hi,

I get the same message. As far as I know is just a warning message, you should import the relevant PGP signature to get rid of it.
Package installation is not affected as far as I can tell.

Regards

---

