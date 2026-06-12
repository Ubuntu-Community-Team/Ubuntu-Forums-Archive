---
title: "amule... no way!!"
date: 2005-07-09
forum: General Help
---

### Post by lucaflea on 2005-07-09
hi. i can't configure amule...there's no way to download and install it from synaptic. it says 
"W: Errore nello scaricamento di [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/)**libglib1.2_1.2.10-9_amd64.deb**
  Somma MD5 non corrispondente
"
libglib1.2_1.2.10-9_amd64.deb is one of the files he misses...
 
why? why? is there another way to install amule?

---

### Post by titus1950 on 2005-07-10
[QUOTE=lucaflea]hi. i can't configure amule...there's no way to download and install it from synaptic. it says 
"W: Errore nello scaricamento di [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/)**libglib1.2_1.2.10-9_amd64.deb**
  Somma MD5 non corrispondente
"
libglib1.2_1.2.10-9_amd64.deb is one of the files he misses...
 
why? why? is there another way to install amule?[/QUOTE]
  I had problems with amule also...

If you need a good p2p client  try **Limewire** is easy to install and it works great
[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

Good luck...

---

### Post by adwait on 2005-07-10
Try changing your sources.list to archive.ubuntu.com instead of us.archive.ubuntu.com because on my end it works fine.

to change the source.list file:
sudo gedit /etc/apt/sources.list

---

### Post by Tad030 on 2005-07-10
I was able to install amule, but whenever I try to search for a file, no matches are ever found - I'm not sure why.  amule connects to the server just fine, so it isn't that.

---

### Post by lucaflea on 2005-07-10
"Try changing your sources.list to archive.ubuntu.com instead of us.archive.ubuntu.com"

i've tried but it returns me always the same error on that file. do i have to do something particular when saving archive.ubuntu.com???

---

### Post by lucaflea on 2005-07-10
[QUOTE=titus1950]I had problems with amule also...

If you need a good p2p client  try **Limewire** is easy to install and it works great
[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

Good luck...[/QUOTE]


i tried this too.... no way! no way!!! it says that it can't find this file "sun-j2re1.5"....

i'm desperate..... :-?

---

### Post by rider343 on 2005-07-10
change your /etc/apt/sources.list


## Uncomment the following two lines to fetch updated software from the network
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by lucaflea on 2005-07-10
great!!!! it works. and so does  amns....

i can't understand why amule looks so..."old style".... i'll look for some skins...

a question (the last....for today): in synaptic i can see some versions of softwares i need...the question is: how can i update (or install the most recent version) of that software?

luca

ubuntu rocks

---

### Post by Tad030 on 2005-07-10
[QUOTE=lucaflea]"Try changing your sources.list to archive.ubuntu.com instead of us.archive.ubuntu.com"

i've tried but it returns me always the same error on that file. do i have to do something particular when saving archive.ubuntu.com???[/QUOTE]
 well, i think i totally screwed myself with amule.  i noticed there was a 2.0.2 release (the version on the unofficial guide was 2.0.0), so i attempted to upgrade amule.  now, i cannot even get the program to open.  moreover, i have no idea how to remove the program to attempt a fresh install.  my add/removes programs feature is not running correctly (the mouse icon just keeps spinning like it is thinking, and nothing happens) and i'm still learning terminal functions, so i'm not sure how to remove there either.  any help would be great.  i used emule in windows, and enjoyed it, i know some folks here have suggested limewire, but i didn't care for the windows version - any different in linux?

---

### Post by lucaflea on 2005-07-10
amule seems to work as well as emule...i hope....

a question: i could install flash plugin but since that moment i couldn't open firefox/mozilla anymore...i removed it and now it works again but always without flash plugin

---

