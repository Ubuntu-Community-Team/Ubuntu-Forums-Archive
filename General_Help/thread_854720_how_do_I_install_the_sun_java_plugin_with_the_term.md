---
title: "how do I install the sun java plugin with the terminal consola?"
date: 2008-07-09
forum: General Help
---

### Post by carioca on 2008-07-09
:confused:

hi, ubuntu linuxers,

how do I install the sun java plugin on ubuntu 8.04 by using the terminal consola? which codes  should I have to type to get it working properly? 

I have read this explanation how to install sun java plugin with the synaptic at this link:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

"By default, Ubuntu doesn't have full multimedia support. Because of patents and copyrights that apply in some countries. However, it's easy to plug in the missing codecs and players yourself. This simple how-to will provide you quickly with 99 % audio and video support.

You'll need several players, because sometimes you'll need to switch players for certain file types. Don't worry: none of the players is bloatware....

Note: full multimedia support is still only available for 32-bit Ubuntu. If you have 64-bit Ubuntu, then you will encounter some problems from time to time.

 

This is how you do it: 

1. Establish internet connection.

2.  Applications - Add/Remove... 

Show: "All available applications" (instead of only the "supported applications") 

Search word: mp3 (don't press Enter, just wait) 

Tick:

- Ubuntu restricted extras

- Gstreamer extra plugins

- Gstreamer ffmpeg plugin

- VLC media player

- Mplayer Movie player

- gxine

- Audacious

Click Apply and agree to all proposed answers in the dialogue windows (popups).

When it's finished, close Add/remove.

 

3. System - Administration - Synaptic Package Manager

Press the "Search" button in the toolbar of Synaptic. 

Search word: openjdk

Mark openjdk-6-jre and openjdk-6-jre-headless for complete removal (openjdk is still inadequate for many websites). The IcedTea plugin will be removed automatically as well, which is what you want.

Click Apply.

 

4. Still in Synaptic, install Sun Java as follows:

Search words: sun java 

Tick: sun-java6-jre and sun-java6-plugin

Click Apply.

When prompted, agree to Sun's licence agreement by ticking the box before the line "Do you agree... (etc)".

 

5. In Synaptic, install this necessary systemwide plugin in Firefox, as follows:

Search words: vlc plugin 

Tick: mozilla-plugin-vlc

Click Apply.

When it's finished, close Synaptic. 

That takes care of 99 % of multimedia support. Next: the missing 1 %"


I'd appreciate your hints. Best Regards. 


:guitar:

:lolflag:

---

### Post by arm-c on 2008-07-09
Sorry, but I don't understand what your question is.

---

### Post by ettercap on 2008-07-09
to install java..

sudo apt-get install <selected package>

in place of the <selected package> type the following

 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm

---

### Post by zeronothing on 2008-07-10
if you would like to be able to install packages and search for packages in terminal use the command "Aptitude." Aptitude is a console package manager. Kind of like Synaptic in ubuntu but only at the commandline level. If you were to do the command "Aptitude search sun-java" (at the console level) you would be given some results based on what you provided. Once you do the search you can use the command "aptitude install package" and it will install whatever program you would like. To answer your question to executing this command at the console "sudo aptitude install sun-java6-jre." hopefully this will install java for you. once you do that you may need to set the default java program to use. you can do this at the commandline by issuing the command "update-java-alternative -l" and this will list all of the java versions installed. so now in order to set the one to default you will need to issue this command "sudo update-java-alternative -s whatever verison you like." hopefully this will help. if you haven't all ready try installing the ubuntu-restricted-extras package. its usually quite useful and I think it includes sun-java6 package.

---

### Post by zvacet on 2008-07-10
If you need only java-plugin 

```
sudo aptitude install sun-java6-plugin
```

You can read [this]("https://help.ubuntu.com/community/Java") if you want to know more about Java and Ubuntu.

---

### Post by carioca on 2008-07-10
:)

thank you, fellows, I got it installed by consola terminal.I think I'm an oldfashioned user, for the reason I like best the terminals. I'd rather use it better than synaptic,I didn't get used to handle with the synaptic. by the way, do you know a site to check if it's working properly? God bless you! Best regards.


:lolflag:

---

