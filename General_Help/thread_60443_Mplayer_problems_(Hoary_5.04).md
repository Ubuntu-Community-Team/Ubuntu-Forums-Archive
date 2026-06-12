---
title: "Mplayer problems (Hoary 5.04)"
date: 2005-08-27
forum: General Help
---

### Post by chumbo on 2005-08-27
This is quite strange, 

I have installed mplayer using apt-get.. when I start it from command line (regardless of the content I'm trying to play - i.e. it happens for all formats) it looks like it's playing (i.e. there are no obvious errors displayed, cdrom spins) yet there is no video nor audio output of any kind.

I'm attaching the output,

any help is greatly appreciated..

Chumbo

P.S.
changing to vo=xv in config don't seem to do anything either

---

### Post by arnieboy on 2005-08-27
[QUOTE=chumbo]This is quite strange, 

I have installed mplayer using apt-get.. when I start it from command line (regardless of the content I'm trying to play - i.e. it happens for all formats) it looks like it's playing (i.e. there are no obvious errors displayed, cdrom spins) yet there is no video nor audio output of any kind.

I'm attaching the output,

any help is greatly appreciated..

Chumbo

P.S.
changing to vo=xv in config don't seem to do anything either[/QUOTE]

Please paste the contents of /etc/mplayer/mplayer.conf 
also do a sudo apt-get install mplayer-fonts 
if u havent installed mplayer-fonts yet.

---

### Post by spin2cool on 2005-08-28
Do you have the proper video drivers installed?

---

### Post by chumbo on 2005-08-28
[QUOTE=spin2cool]Do you have the proper video drivers installed?[/QUOTE]

I believe so, there's nothing to make me believe that something is amiss (Ubuntu installed and booted straight into X at the proper res etc). I'm using "Intel Corp. 82852/855GM Integrated Graphics Device".

If I do it by invoking gmplayer (gui mode) and attempt to play it just hangs (the whole thing goes non-responsive) eventually (whenI kill the process) it shows a dialog saying "MPlayer interrupted by signal 15 in module: ao2_init"?!

I've also tried to copy an entire mplayer.conf from etc to my .mplayer as well as installing mplayer-fonts.. no luck..

Any ideas are appreciated..

Chumbo

---

### Post by chumbo on 2005-08-31
[QUOTE=chumbo]I believe so, there's nothing to make me believe that something is amiss (Ubuntu installed and booted straight into X at the proper res etc). I'm using "Intel Corp. 82852/855GM Integrated Graphics Device".

If I do it by invoking gmplayer (gui mode) and attempt to play it just hangs (the whole thing goes non-responsive) eventually (whenI kill the process) it shows a dialog saying "MPlayer interrupted by signal 15 in module: ao2_init"?!

I've also tried to copy an entire mplayer.conf from etc to my .mplayer as well as installing mplayer-fonts.. no luck..

Any ideas are appreciated..

Chumbo[/QUOTE]
 For what it's worth (there seems to be quite a few people out there having problems with mplayer) - I found the culprit - something is wrong with my audio. So, the command " mplayer -ao null /media/cdrom0/Steal_XVID_AC3.avi" works just fine (albeit without sound ;-), anything else for "ao" and it freezes - this is surprising as the install managed to detect the soundcard right away.

Again,

If anyone has any ideas, it's greatly appreciated..

---

### Post by Perfect Storm on 2005-08-31
If everything turns into hell regarding mplayer, you try out some othe media player like VCL or xine.

By the way did you installed the multimedia codecs? [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by bob k on 2005-08-31
I gave up on mplayer with this release and switched to totem. if you have already downloaded the codecs from mplayer and are installed in the correct directory.

If you installed mplayer from synaptic then mark it for removal and if you installed the mplayerplug-in(needs alot of work) than mark it for compleate removal.

If you don't know if the plugin is installed go to the address bar in firefox and enter about:plugins.

once the mplayerplug-in has been removed the only plugins I have left are:

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.552 built with gcc 3.2.0 on May 13 2005

    File name: libflashplayer.so
    Shockwave Flash 7.0 r25

At this point you will be asked for a plugin select browse to /user/bin/totem.

Playing a dvd works good although full screen does not work quite right. but I had a problem close to the same problem with mplayer. some times it works and some times it don't.

I have not traced it down and don't have the time, but from what I have seen it looks like GTK is supplying the  codec with (screen size - the gtk widget controls) or the codec is interpeting the screen size wrong.

Bob

---

### Post by petr on 2005-09-07
Im giving up on mplayer gxine is what I am now using.
Petr :???:

---

### Post by karimw786 on 2005-09-21
[QUOTE=petr]Im giving up on mplayer gxine is what I am now using.
Petr :???:[/QUOTE]

Same here!  One thing though: how to I get gxine to work with firefox?  Is there a firefox plugin?  HELPPPPPPP!! ;)

---

### Post by fordfan753 on 2005-09-22
[QUOTE=chumbo]For what it's worth (there seems to be quite a few people out there having problems with mplayer) - I found the culprit - something is wrong with my audio. So, the command " mplayer -ao null /media/cdrom0/Steal_XVID_AC3.avi" works just fine (albeit without sound ;-), anything else for "ao" and it freezes - this is surprising as the install managed to detect the soundcard right away.

Again,

If anyone has any ideas, it's greatly appreciated..[/QUOTE]

I have a friend with the same sort of problem...mplayer would just crash. New Toshiba 12.1", beefy Centrino with 512MB RAM, and yet mplayer would just crash. I tried various mplayer versions and even different architechure versions on fresh installs, and older installs, and I think I even tried a Debian install, just to try to get it to work. But after all that, and no luck, I just got him using Xine. (an awesome program in it's own right)

---

