---
title: "wmv files"
date: 2005-09-28
forum: General Help
---

### Post by jdg on 2005-09-28
how to make wmv files play in totem? i already followed the guide to install codecs in the restrcited formats page but i get this error.

> Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


---

### Post by stoeptegel on 2005-09-28
win32codecs is not in the ubuntu repositories anymore due to legal issues, you have to find another source. Trigger the search, there are lots of topics with this question..

---

### Post by jdg on 2005-09-29
can someone send or give me a link where i can get the w32 codec?

---

### Post by tehwa on 2005-09-29
A quick google search leads me to this page:

[http://nozell.com/blog/archives/2005/07/22/w32codecs-for-ubuntu-hoary/](http://nozell.com/blog/archives/2005/07/22/w32codecs-for-ubuntu-hoary/)

Take note of the user comment left just below the story.

---

### Post by jdg on 2005-09-29
tnx! btw how do i install w32codec from this link?

[ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/)

---

### Post by tehwa on 2005-09-29
[QUOTE=jdg]tnx! btw how do i install w32codec from this link?
[ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/)[/QUOTE]
I think the poster is suggesting that you modify the line

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

to say

deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) testing main

However, I haven't tested these. You may as well just add the first address to the repos list and install, disregard the second address unless there's stuff there you need.

---

### Post by jdg on 2005-09-29
i already tried them both and both failed. :(

---

### Post by tehwa on 2005-09-29
[QUOTE=jdg]i already tried them both and both failed. :([/QUOTE]
Sorry tiger, I hadn't tested when I posted previously. I have tested this and it works.
Add this line to the end of /etc/apt/sources.list:
```
deb ftp://cipherfunk.org/pub/packages/ubuntu/ hoary main
```
then:
```

sudo apt-get update \ 
sudo apt-get install w32codecs
```

---

### Post by jdg on 2005-09-29
thanks man! it worked great!:p 

but i got this error when i updated is this ok? 
> W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) hoary Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: You may want to run apt-get update to correct these problems


---

### Post by ubuntu_demon on 2005-10-05
[QUOTE=jdg]thanks man! it worked great!:p 

but i got this error when i updated is this ok?[/QUOTE]
yeah no problem there

---

### Post by spencer on 2005-10-05
This HowTo May help.
[http://www.ubuntuforums.org/showthread.php?t=70227](http://www.ubuntuforums.org/showthread.php?t=70227)

---

### Post by ghostintheshell on 2005-10-05
[http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23]("http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23")

It's Easy Ubuntu 2.3 (translated in English) from the french people ;)
(also, we don't have this b*llsh*t legal issue in Europe thanks to smart people - *no banana union /*[SIZE=-1]* no software patents*[/SIZE]).

If you want to do this automated part of EasyUbuntu manually:

codecs (wmv, ...) ->
```

wget -c http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-20050412.tar.bz2
tar xvjpf all-20050412.tar.bz2[FONT=monospace]
[/FONT]mv all-20050412 /usr/lib/codecs[FONT=monospace]
[/FONT]ln -s /usr/lib/codecs/ /usr/lib/win32

``` 

package (ogg, ...) ->
```

apt-get --assume-yes --force-yes install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg gstreamer0.8-pitfdll libdvdcss2 libxvidcore divx4linux lame ffmpeg mjpegtools vorbis-tools mpg321
gst-register-0.8

``` 

enjoy our freedom.

---

### Post by Protostar on 2005-10-06
WOOH! Thanks guys. It worked for me too. I'm so happy.:)

---

### Post by RaoulDAndrezy on 2005-10-08
> **ghostintheshell][http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23]("http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23")

It's Easy Ubuntu 2.3 (translated in English) from the french people  said:**
> * no software patents*[/SIZE]).


Note that there is absolutly no relation software patents <-> w32codecs. w32codecs are proprietary dlls distributed (and sometimes modified) in violation of there respectives licences. It's illegal in France, and in European Union like in US.
In france it can cost 3 years in jail and 300,000 euros ;)

---

### Post by ghostintheshell on 2005-10-08
[quote=RaoulDAndrezy]Note that there is absolutly no relation software patents <-> w32codecs. w32codecs are proprietary dlls distributed (and sometimes modified) in violation of there respectives licences. It's illegal in France, and in European Union like in US.
In france it can cost 3 years in jail and 300,000 euros ;)[/quote] 
Then, jails have to be bigger all over the World (except in USA of course) ...

Big kisses to the USA and B. Gates & co, makers of criminals  ;-)

---

