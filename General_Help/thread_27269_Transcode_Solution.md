---
title: "Transcode Solution"
date: 2005-04-15
forum: General Help
---

### Post by mcclane on 2005-04-15
Anyone still having trouble installing Transcode ?

Well heres what worked for me. I simply commented the "testing" line of the marillat repository. 

i.e > 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

And all of backports. 

 \\:D/

---

### Post by artinla on 2005-04-15
OMG yes I am having trouble.  I am going to try your fix right now.

Thanks

Art

---

### Post by shakin on 2005-04-15
Oh, dammit. And I just put up a how-to about installing DVD Decrypter under Wine. Oh well, DVD Decrypter is still a nice utility and I'm sure many people will still want to use it.

[Read my how-to](http://ubuntuforums.org/showthread.php?t=27369)

---

### Post by artinla on 2005-04-16
Hey I got both things working thanks to your help.  It works!!

Thanks

Art

---

### Post by shakin on 2005-04-16
[QUOTE=mcclane]Anyone still having trouble installing Transcode ?

Well heres what worked for me. I simply commented the "testing" line of the marillat repository. 

i.e > 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

And all of backports. 

 \\:D/[/QUOTE]


Where is libdvdread2? libdvdread3 is in the Ubuntu repository, but transcode wants libreaddvd2 and it's not in marillat or the Ubuntu main/restricted/universe/multiverse.

---

### Post by abmcr on 2005-04-16
I have this /etc/apt/source.list

andrea@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
 ## Uncomment the following two lines to fetch updated software from the networkdeb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

#deb [http://packages.dotdeb.org](http://packages.dotdeb.org) ./

 If i try  to install dvdrip (apt-get install dvdrip) i have this error message:

andrea@ubuntu:~$ sudo apt-get install dvdrip
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
Alcuni pacchetti non possono essere installati. Questo può voler
dire che è stata richiesta una situazione impossibile oppure, se
si sta usando la distribuzione "unstable", che alcuni pacchetti
richiesti non sono ancora stati creati o rimossi da incoming.

Poichè è stata richiesta solo una singola operazione è molto facile che
il pacchetto semplicemente non sia installabile, si consiglia
di inviare un "bug report" per tale pacchetto.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
  dvdrip: Dipende: transcode (>= 2:0.6.14) ma non sta per essere installato
E: Pacchetto non integro


The dependency with transcode is the problem. What i do? Thank you
 :neutral:

---

### Post by shakin on 2005-04-16
[QUOTE=abmcr]I have this /etc/apt/source.list

{snip}

The dependency with transcode is the problem. What i do? Thank you
 :neutral:[/QUOTE]

I bet you have the same problem as me. Install transcode by itself and it will tell you that you are missing libdvdread2. That's what is causing the dvdrip install to fail.

---

### Post by kiddxaq on 2005-04-16
When I'm trying to install transcode, it gives the error that it needs libdvdread2. However, libdvdread3 is already installed, and libdvdread2 does not show up as an installable package. Is transcode able to use libdvdread3? Also, the same problem occurs with libvorbis0  (libvorbis0a is installed).

---

### Post by Tschaeck on 2005-05-01
for me an other solution works. 

i am using the "testing" repository only and commented the "stable" and "unstable" lines.

---

### Post by dukeinlondon on 2005-05-06
[QUOTE=Tschaeck]for me an other solution works. 

i am using the "testing" repository only and commented the "stable" and "unstable" lines.[/QUOTE]
 that works for me too. thanks

---

### Post by Josh M on 2005-05-08
[QUOTE=Tschaeck]for me an other solution works. 

i am using the "testing" repository only and commented the "stable" and "unstable" lines.[/QUOTE]

This also worked for me, thanks.

---

### Post by capitan.harlock on 2005-05-15
[QUOTE=Josh M]This also worked for me, thanks.[/QUOTE]

Idem, thanks :)

---

### Post by Hep on 2005-08-23
No way, impossible to install transcode and dvdrip ...

---

