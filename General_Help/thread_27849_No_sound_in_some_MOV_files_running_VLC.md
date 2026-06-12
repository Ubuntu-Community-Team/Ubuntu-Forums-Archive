---
title: "No sound in some MOV files running VLC"
date: 2005-04-17
forum: General Help
---

### Post by Turin Turambar on 2005-04-17
Some are ok, some are deaf. Most are produced without any sound. How can I fix that? I'm using the latest VLC found with Synaptic

Also, how come that with "open with other application" option I cannot choose WXVLC by default (says "could not add application), I have to type VLC?

Thanks.

---

### Post by NeoChaosX on 2005-04-17
Strange, I had problems with QuickTime files in players that weren't VLC. Do you have the latest w32codecs installed?

As far as the Application select goes, I think it's a problem with the shortcuts in the menu. You can delete the existing ones and create new VLC shortcuts with the Menu Editor that'll work fine.

---

### Post by Turin Turambar on 2005-04-17
UHhh...no... I didn't install anything with "w32" in it... Besides, I cannot find it in Synaptic?

---

### Post by bored2k on 2005-04-17
[QUOTE=Turin Turambar]UHhh...no... I didn't install anything with "w32" in it... Besides, I cannot find it in Synaptic?[/QUOTE]
 Add this to your /etc/apt/sources.list
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

By doing sudo gedit /etc/apt/sources.list
then sudo apt-get update ; sudo apt-get install w32codecs xine-ui

And retry in xine video player ;). [or vlc]

---

### Post by Turin Turambar on 2005-04-18
I have just discovered that the missing codec is QDM2.

W32 pack is 12-13mb and it would take too long for me to download (dial-up) and I need just one codec (everything else works).

Is there a way for me to DL/install qdm2 codec only?

---

### Post by MaX on 2005-04-18
I have the w32 package, its 34 mb but I don't have sound in Quicktime anyhow.

---

### Post by garfield on 2005-04-20
I installed w32[...] too and I dont have sound in VLC :(

---

### Post by bored2k on 2005-04-20
[QUOTE=garfield]I installed w32[...] too and I dont have sound in VLC :([/QUOTE]
 sudo apt-get install vlc-esd, then go to settings and make vlc use esd. w32 doesn't even touch vlc.

---

### Post by medya on 2006-05-08
>  go to settings and make vlc use esd. w32 doesn't even touch vlc.

where in the setting I can make VLC to use esd?

---

### Post by XxPoseidoNxX on 2008-03-08
I use Quicktime and Wine to play .mov files 
here is a howto:
[HTML]http://wine-review.blogspot.com/2007/08/quicktime-716-on-linux-with-wine.html [/HTML]

---

