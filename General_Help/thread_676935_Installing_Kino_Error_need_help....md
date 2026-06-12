---
title: "Installing Kino Error need help..."
date: 2008-01-24
forum: General Help
---

### Post by tech4 on 2008-01-24
So, I am new user to Ubuntu. I got the ./ confure thing to run all the way through. now when I run the make command I get the following error. The problem is that I don't know enough to understand what it is telling me. Where do I start. Sorry for the newbie question.

make[1]: Entering directory `/home/lotero/Documents/Installs/kino-1.2.0'
Making all in po
make[2]: Entering directory `/home/lotero/Documents/Installs/kino-1.2.0/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/lotero/Documents/Installs/kino-1.2.0/po'
Making all in ffmpeg
make[2]: Entering directory `/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg'
"/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg"/version.sh "/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg"
/bin/sh: /home/lotero/Documents/Installs/kino-1.2.0/ffmpeg/version.sh: Permission denied
make -C libavutil   all
make[3]: Entering directory `/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg/libavutil'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg/libavutil'
make -C libavcodec  all
make[3]: Entering directory `/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg/libavcodec'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg/libavcodec'
make -C libavformat all
make[3]: Entering directory `/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg/libavformat'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg/libavformat'
make -C vhook all
make[3]: Entering directory `/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg/vhook'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg/vhook'
make[2]: Leaving directory `/home/lotero/Documents/Installs/kino-1.2.0/ffmpeg'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lotero/Documents/Installs/kino-1.2.0'
make: *** [all] Error 2

What does these errors mean?

Tech4

---

### Post by eggdeng on 2008-01-24
Why are you installing from source? You can install quickly and easily from the repos with
```
sudo apt-get install kino
```

---

### Post by tech4 on 2008-01-28
Umm, I was installing from the source because I'm a Newbie and didn't know better. Thanks for the tip. I just wish I new that earlier. But, how to you fix the errors. Just in case it happens again.


Tech

---

