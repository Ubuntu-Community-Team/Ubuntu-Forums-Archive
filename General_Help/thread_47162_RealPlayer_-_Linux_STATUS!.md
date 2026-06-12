---
title: "RealPlayer - Linux STATUS!"
date: 2005-07-07
forum: General Help
---

### Post by Shinitenshi on 2005-07-07
Ok i downloaded the linux version or real player and i installed it in /home/shinitenshi/My Programs/RealPlayer

[http://www.real.com/player/?src=realplayer](http://www.real.com/player/?src=realplayer)

Now i followed the install instruction on how to install the .bin file. Sweet i got that far now that everything is install how do i make it run >.< <---- total nub

Theres nothing about it on the readme file.

Thnx

---

### Post by intangible on 2005-07-07
You should be able to just type "realplay" in the run box or a terminal to start it, but the better way to install it would be to do it "The Ubuntu Way"

First make sure the "multiverse" repository is enabled, [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
and then:
**sudo apt-get install realplayer**
it will tell you to download a specific file to finish the install and there ya go, you will have a realplayer entry in your menus and everything.

---

### Post by byen on 2005-07-07
[QUOTE=intangible]You should be able to just type "realplay" in the run box or a terminal to start it, but the better way to install it would be to do it "The Ubuntu Way"

First make sure the "multiverse" repository is enabled, [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
and then:
**sudo apt-get install realplayer**
it will tell you to download a specific file to finish the install and there ya go, you will have a realplayer entry in your menus and everything.[/QUOTE]
 sorry to butt-in but i have a similar problem as well...hope u dont mind...

ok i do that and i get 
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  realplayer: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages

what now?  

thanks for the help.

---

### Post by Shinitenshi on 2005-07-07
hmmm i click the icon but dosnt do it >.< do i have to reboot?

---

### Post by Shinitenshi on 2005-07-07
Well i installed everything and now when i click the button it wont play it i must have done somthing wrong. i edited that file and did update  / install and nofin

---

### Post by intangible on 2005-07-07
Ah, i think I know what's going wrong, realplay tries to access the sound device, but it's already locked by Gnome.

Open a terminal and type this: **killall esd** and then try to start real player, if that works, you'll need to do a work around to allow multiple programs to access the sound device at once.  
I made a howto for that purpose here: [thread]44753[/thread]

---

### Post by Shinitenshi on 2005-07-07
[QUOTE=intangible]Ah, i think I know what's going wrong, realplay tries to access the sound device, but it's already locked by Gnome.

Open a terminal and type this: **killall esd** and then try to start real player, if that works, you'll need to do a work around to allow multiple programs to access the sound device at once.  
I made a howto for that purpose here: [thread]44753[/thread][/QUOTE]


wow dude <3 one i typed that in it worked :) is that all i have to do 

sound kinda statiky :P but it works :)

---

### Post by intangible on 2005-07-07
You'll have to follow that howto to make it work effortlessly all the time, or you can just manually type that command before you run realplayer, then type **esd** afterwards to restart your gnome sounds.

---

### Post by Shinitenshi on 2005-07-07
[QUOTE=intangible]You'll have to follow that howto to make it work effortlessly all the time, or you can just manually type that command before you run realplayer, then type **esd** afterwards to restart your gnome sounds.[/QUOTE]

So is there a way to fix the real player sound? its ucky but i can stand it

---

### Post by NeoChaosX on 2005-07-07
There's a way to fix RealPlayer so it works with ESD.

If you've already set up ALSA to do sound mixing and OSS emulation, follow the instructions in [this](http://ubuntuforums.org/showpost.php?p=80282&postcount=21) post to get RealPlayer to work with other apps. Otherwise, you'd have to close all other apps that use sound before you can start Real.

---

### Post by jchaparr on 2005-07-08
OK. I got the same problem as byen:

The following packages have unmet dependencies:
  realplayer: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages

I went through the ALSA how-to (kick-ass, intangible, you got my mplayer working, props, thnx so much) and i have the extra repositories. I'm intent on fixing this.

---

### Post by NeoChaosX on 2005-07-08
Post the contents of /etc/apt/sources.list. None of the official Ubuntu or Backport repos require a higher version of libc than the one included in Hoary.

---

### Post by jchaparr on 2005-07-08
OK. sudo gedit /etc/apt/sources.list gets this:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
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

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

---

### Post by Shinitenshi on 2005-07-08
Thnx guys sound rox once again :) <3 u guys!

---

### Post by NeoChaosX on 2005-07-09
jchaparr: For the love all that is holy, remove the Marillat repo. That's your problem. THe packages there are meant for Debian, not Ubuntu. Trying to install it's packages on Ubuntu can cause disaster.

---

### Post by jchaparr on 2005-07-09
OH, sry, lol, total new guy here. How do i remove it? (i assume i start by deleting it from the sources.list)
EDIT:
OK. I commented out the marillat thing. I logged in as the root user and installed realplayer (from the sudo apt-get realplayer), reset a few times and now it's working. Now i can listen to the radio. it's amazing. god bless. <3 u guyz
EDIT 2:
Uh oh. OK. I'm in trouble. I can listen fine to Prairie Home Companion, but that's just audio. Now when I tried to watch any of the No Doubt videos ([http://www.nodoubt.com/visual/varchive.html](http://www.nodoubt.com/visual/varchive.html)) they came up with only audio.
Same for Garbage ([http://www.garbage.com/discog/#](http://www.garbage.com/discog/#)) no video plays, only audio. Any ideas?
EDIT 3:
Uninstalled it, installed it again. Now it's friendly and will play videos perfect. Thanx guys!!

---

