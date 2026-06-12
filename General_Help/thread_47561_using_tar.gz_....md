---
title: "using tar.gz ..."
date: 2005-07-09
forum: General Help
---

### Post by lucaflea on 2005-07-09
hi. i have (after 3 days...) my ubuntu ready, and my interntet connection too (thanx launde). 
now i'd like to install some softwares i need (i.e. Amsn, Amule and a mp3 player). i found on the net some tar.gz files but i can't open them.... (i need them because i have to install the macromedia flash plugin too...).

how can i do ??
luca ](*,)

---

### Post by Matchless on 2005-07-09
[QUOTE=lucaflea]hi. i have (after 3 days...) my ubuntu ready, and my interntet connection too (thanx launde). 
now i'd like to install some softwares i need (i.e. Amsn, Amule and a mp3 player). i found on the net some tar.gz files but i can't open them.... (i need them because i have to install the macromedia flash plugin too...).

how can i do ??
luca ](*,)[/QUOTE]

lucaflea,
             Enable repositories and use Kynaptics or rather Synaptics to install. I have checked Amsn, amule and XMMS are all there for your enjoyment!
Regards
Matchless

---

### Post by lucaflea on 2005-07-09
ehm....
can you please guide me?? i don't know what's "enable repositories" but i'm ready to learn! ;-)

---

### Post by Matchless on 2005-07-09
[QUOTE=lucaflea]ehm....
can you please guide me?? i don't know what's "enable repositories" but i'm ready to learn! ;-)[/QUOTE]

lucaflea,
            Go to here [http://kudos.berlios.de/kf/kisimlar/swmgmt.html](http://kudos.berlios.de/kf/kisimlar/swmgmt.html) and you wil find all the info you may need. I suggest also installing Krusader File manager. Basically you have to edit the file Sources.list from root in the terminal.
sudo kwrite /etc/apt/sources.list or use gedit in place of kwrite if using Gnome.
Good luck. 
Matchless :wink:

---

### Post by lucaflea on 2005-07-09
no way....i can't understand what to do....

sorry....

---

### Post by sapo on 2005-07-09
[QUOTE=lucaflea]no way....i can't understand what to do....

sorry....[/QUOTE]

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

just do it:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

```

then paste this:

```

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Hit Ctrl + S to save, and type this in a terminal:

```

sudo apt-get update
sudo apt-get install amsn xmms amule

```

Done! :grin:

---

### Post by lucaflea on 2005-07-09
great! but it returns me this

"E: Impossibile aprire il file di lock /var/lib/apt/lists/lock - open (13 Permission denied)"

if i double click on a tar.gz it still won't open....

thanx for your help

---

### Post by lucaflea on 2005-07-09
and if i try again to do what you wrote it returns me:

"Impossibile ottenere [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-9_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-9_amd64.deb)  Somma MD5 non corrispondente
Impossibile ottenere [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib+png2/imlib1_1.9.14-16.2ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib+png2/imlib1_1.9.14-16.2ubuntu2_amd64.deb)  Somma MD5 non corrispondente
E: Impossibile prendere alcuni archivi, forse è meglio eseguire apt-get update o provare l'opzione --fix-missing
"

---

### Post by sapo on 2005-07-09
[QUOTE=lucaflea]great! but it returns me this

"E: Impossibile aprire il file di lock /var/lib/apt/lists/lock - open (13 Permission denied)"

if i double click on a tar.gz it still won't open....

thanx for your help[/QUOTE]

Close your synaptic before doing the apt-get stuff  :-P

---

### Post by lucaflea on 2005-07-09
it is closed.... but the amsn package can't be installed....

i reopened synaptic and i can see amsn xmms etc. but when i try to install them it returns me alway 
"Impossibile ottenere [http://us.archive.ubuntu.com/ubuntu....10-9_amd64.deb](http://us.archive.ubuntu.com/ubuntu....10-9_amd64.deb) Somma MD5 non corrispondente"

---

### Post by Matchless on 2005-07-09
I am not actually sure exactly what you are getting. Is it a warning that one of the links in the deposity is not picked up, then just click OK and wait til synaptics have finished the dependancies at the bottom. Then check if the tick box is green, which means the app is installed. you are obviously checking the ap tick box to be installed and the clicking apply?
If the app is already installed you may have to create a desktop icon yourself for most as not all are automatically installed. Right click, desktop launcher and enter the file name in the command block.
Hope this helps
Matchless

---

### Post by mohaham on 2005-07-09
lucaflea,

here's a step by step guide..

amule
[http://ubuntuguide.org/#amule](http://ubuntuguide.org/#amule)
mp3 player
[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
[http://ubuntuguide.org/#xmms](http://ubuntuguide.org/#xmms)

---

### Post by lucaflea on 2005-07-09
thanx guys but with amsn, amule and xmms it says that it can't pick up package and to try " --fix-missing" what is it???

i read the guide and i installed some softwares i need!! i understood howto!
i'm using gaim instead of amsn and xine (i think it sucks) instead of xmms...
but amule doesn't work. and synoptic can't detect flash plugin....

---

