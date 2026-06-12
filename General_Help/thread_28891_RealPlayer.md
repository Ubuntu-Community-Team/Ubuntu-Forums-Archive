---
title: "RealPlayer"
date: 2005-04-22
forum: General Help
---

### Post by ubuntu27 on 2005-04-22
HI everybody.

I installed RealPlayer that I download from the Real.com website [http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=linuxHomePage&pageregion=install_instructions&src=realhome_linux_0_2_1_0_0_3&pcode=rn&opage=realhome_linux](http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=linuxHomePage&pageregion=install_instructions&src=realhome_linux_0_2_1_0_0_3&pcode=rn&opage=realhome_linux)

But, unfortunately, it seems I installed incorrectly. (RealPlyer won't open at all)

So, I want to know how to UNISTALL IT, so I could REinstall it.

Please, help me.

---

### Post by SGC on 2005-04-22
Open synaptic from:
System > adminstration > synaptic package manager

click on the search button and type: realplayer 

if real player is installed, you will find a green squre behind it, else there is a white squre. 

from the search result right click on the real player and choose mark for removal then hit the apply button

---

### Post by ubuntu27 on 2005-04-22
[QUOTE=SGC]Open synaptic from:

if real player is installed, you will find a green squre behind it, else there is a white squre. 

[/QUOTE]

That's weird. I installed and, I CAN find RealPlayer in "Applicatiions/Sound and Video/RealPlayer 10" but, when I search for RealPlayer in synaptic package manager. It displays a white square.... and it even says that is version 8 !!! [Look for the pic that I uploaded (attached) ]

---

### Post by SGC on 2005-04-22
It seems like a common problem, when i install realplayer it also does not work in the begging.

but after i follow the instruction in this post, it works:
[http://www.ubuntuforums.org/showthread.php?t=14499&highlight=uninstall+realplayer](http://www.ubuntuforums.org/showthread.php?t=14499&highlight=uninstall+realplayer)

you need to go to the following:
System > preferences > sound

then uncheck the following: 
Unable sound server startup

after that realplayer will work!

---

### Post by ubuntu27 on 2005-04-22
Yes, it seems it is a commun problem. I found it in many Threads...
But the thing is that I wish there were a solution without unchecking the Unable sound server startup....

---

### Post by ubuntu27 on 2005-04-22
By the way. Look everybody what Real says in their "Read me" file:

This is the readme file for the RealPlayer
   10.0.4.750 release. This file will be
   modified as we have more information -
   so please do check our website
   periodically for new and updated
   information.

  What's New in 10.0.4.750

   This version is a security update.

  Known Issues

     * If you are having problems playing
       back media and are behind a proxy
       you can try using rtsp transport via
       http only (go to transports pane in
       prefs, select "use specified
       transport" and click "configure
       rtsp." Then uncheck "attempt
       multicast," "attempt udp," and
       "attempt tcp.")
     * Context Menu might not work while
       managing favorites with older GTK
       versions.
     * If RealPlayer 8 is installed on the
       system (via rpm) the RealPlayer 10
       rpm does not remove RP8 before
       installing RP10. This means that RP8
       and RP10 coexist on the same system.
       In the event that this configuration
       results in any problems with the
       embedded player (plugin) please
       delete the file rpnp.so from your
       mozilla plugins directory. (issue
       #2678)
     * Some content encoded in RealAudio 3
       fails to play. Multimedia content
       that uses RA3 as the audio codec
       will still play without audio. RA3
       has been deprecated.
     * Player does not play gnome-vfs URI's
       (smb://). Workaround is to mount the
       samba share using smbmount etc
       (issue #2269).
     * Alsa and esound drivers are not
       included in this build
       The OSS device used for playback can
       be set using the AUDIO environment
       variable. eg export AUDIO=/dev/dsp2
     * See the Helix Player bug tracker for
       a list of the latest issues that
       affect the player.
     * The value of the UDPPort preference,
       if used, needs to be set as a range,
       for example:

        UseUDPPort=1
        UDPPort=7000-7010

       Setting it to a single number
       will result in a player crash.

Technical Support

   Support pages for the RealPlayer for
   Linux are available at
   [http://service.real.com](http://service.real.com). Click on
   RealPlayer and choose RealPlayer 10 for
   Linux/Unix from the drop down list.

   To reach the development team please
   send email to
   [email]users@player.helixcommunity.org[/email].

   You can check the player help page in
   the Helix Player project:
   [http://player.helixcommunity.org](http://player.helixcommunity.org)

   Thank you for using the RealPlayer!

---

### Post by SGC on 2005-04-22
If you are using realplayer just for realmedia format, you can install w32codecs to play those files in another player.

---

### Post by ubuntu27 on 2005-04-22
Well, What I wanna do is to listen to the live Radio...
you know there are many Websites that offer to listen to their radios or amm... well, you knwo what I mean... ONLINE BROADCASTING. That's the word...

---

### Post by Holdem on 2005-06-11
[QUOTE=SGC]It seems like a common problem, when i install realplayer it also does not work in the begging.

but after i follow the instruction in this post, it works:
[http://www.ubuntuforums.org/showthread.php?t=14499&highlight=uninstall+realplayer](http://www.ubuntuforums.org/showthread.php?t=14499&highlight=uninstall+realplayer)

you need to go to the following:
System > preferences > sound

then uncheck the following: 
Unable sound server startup

after that realplayer will work![/QUOTE]
Cool-now it works.
And whats more surprising is that I found this post and didn't need to post another.  \\:D/ 
Just moved over from Mandriva (total Linux time 2months) and Ubuntu is a lot eaisier on the install side.

---

### Post by Musashi on 2005-06-14
[QUOTE=Holdem]Cool-now it works.
And whats more surprising is that I found this post and didn't need to post another.  \\:D/ 
Just moved over from Mandriva (total Linux time 2months) and Ubuntu is a lot eaisier on the install side.[/QUOTE]

Before start realplayer do in a terminal:

"sudo killall esd"

After that realplayer will open.

---

