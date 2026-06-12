---
title: "Sound in flash"
date: 2005-04-07
forum: General Help
---

### Post by Spug on 2005-04-07
I have installed the Macromedia Flash Player for Opera (which is Mozilla plug-in compatible). It now plays flash movies like a charm. However, there is no sound. I get sound if I run Opera as root, so I am guessing I need to add myself to some group which is not the audio group, because I belong to that one already. What group is it, or what do I need to do if it is not a permission problem?

---

### Post by adbak on 2005-04-08
[QUOTE=Spug]I have installed the Macromedia Flash Player for Opera (which is Mozilla plug-in compatible). It now plays flash movies like a charm. However, there is no sound. I get sound if I run Opera as root, so I am guessing I need to add myself to some group which is not the audio group, because I belong to that one already. What group is it, or what do I need to do if it is not a permission problem?[/QUOTE]
 I don't know if this will work as I don't use Opera, but if it is Mozilla plug-in compatible then it just might:  apt-get the package "flashplayer-mozilla" and install it.  You may have to symlink your Firefox plugins folder to your Opera one.  Good luck.

---

### Post by jeremy on 2005-04-09
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

---

### Post by Spug on 2005-04-17
[QUOTE=jeremy]sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1[/QUOTE]
 Thanks bunches and sorry for the bump. That last one worked like a charm! :D

---

### Post by therabbit on 2005-05-20
Mine's sorted now too. Thankyou!

---

### Post by Rodrigo on 2005-05-20
superb solution thanks!

---

### Post by wh0rd on 2005-08-19
> sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1 

It worked charmingly, but would it be too much to ask you what's going on in that command or anyone else who has an idea of it.

---

### Post by MetalMusicAddict on 2005-08-19
[QUOTE=wh0rd]It worked charmingly, but would it be too much to ask you what's going on in that command or anyone else who has an idea of it.[/QUOTE]
Got me going also! Weird. What does this do? Hope this is fixed in Breezy. Or is it even their issue?

---

### Post by gusto5 on 2005-09-06
[QUOTE=jeremy]sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1[/QUOTE]

this has fixed for me also. can someone explain to me WHY This fixes it?

---

### Post by kevcart3 on 2005-09-07
Firefox uses libesd.so.1 and doesn't look for libesd.so.0, so what you are doing it making a symbolic link that points to libesd.so.1 so that Firefox knows where to look.

Hope this helps explain it.  :)

---

### Post by endangst on 2006-01-01
Hi there.  This doesn't work for me.  I'm using Ubuntu 5.10 and received a New Year's greeting card from a friend.  I use Firefox 1.5 and it asked me to install Macromedia Flash.

I installed the Flash plugin, but I can't get any sound.  I also tried sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1 but that didn't make any difference... still no sound for Flash greeting cards.

MP3, WMA, etc all works fine though, as so system sounds.

Any help is greatly appreciated.

---

### Post by fealz on 2006-01-09
my friend is having the same problem... any other solutions?

---

### Post by danish_demon on 2006-01-31
i am having the same problem, and already did the aforementioned symbolic link command.  anything else?  is there any way to move this to the breezy forum since it appears most of the people with this problem are running breezy now?

---

### Post by ricardo.chavez on 2006-02-22
dunno if this is useful now, but this thread:
[http://www.ubuntuforums.org/showthread.php?t=101438&highlight=flash+plugin+firefox+sound](http://www.ubuntuforums.org/showthread.php?t=101438&highlight=flash+plugin+firefox+sound)
has the solution.

as an aditional tip, you can turn /usr/bin/firefox into a symlink to the script that launches firefox via aoss. that way, you don't mess up your default Web browser and your launchers

**EDIT**: I found out that commenting out the 'killall esd' line allowed me to play a Flash with sound and listen to Rhythmbox while still being able to hear the system sounds (the sounds played when an error dialog pops up or a launcher is clicked). works for me at least...

---

