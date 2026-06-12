---
title: "Best desktop search?"
date: 2005-07-05
forum: General Help
---

### Post by gammyhand on 2005-07-05
Best desktop search...I installed it but when I run it (after rebooting) nothing happens. It seems to load and then all goes quiet. What is it? How is it working? And is it useful?

---

### Post by varunus on 2005-07-05
Did you install Beagle?  BEST is just a frontend for beagle, a howto on it can be found here:
[http://www.beaglewiki.org/Ubuntu_Installation](http://www.beaglewiki.org/Ubuntu_Installation) 

Make sure beagled is running before you use best.  (Just type "beagled" into the run application box in GNOME before you start BEST.  Adding it to your session startup programs works too.)

---

### Post by gammyhand on 2005-07-05
[QUOTE=varunus]Did you install Beagle?  BEST is just a frontend for beagle, a howto on it can be found here:
[http://www.beaglewiki.org/Ubuntu_Installation](http://www.beaglewiki.org/Ubuntu_Installation) 

Make sure beagled is running before you use best.  (Just type "beagled" into the run application box in GNOME before you start BEST.  Adding it to your session startup programs works too.)[/QUOTE]
According to synaptic beagle is installed. When I start best it grinds the disc for a second, I occasionally see a window open momentarily. And then thats it...?

---

### Post by gammyhand on 2005-07-06
[QUOTE=gammyhand]According to synaptic beagle is installed. When I start best it grinds the disc for a second, I occasionally see a window open momentarily. And then thats it...?[/QUOTE]
 OK, I looked at the beagle log file and it says I need to set up extended permissions. So I went to the beagle wiki and found out what to do. The problem is it says to add this line to fstab:

/dev/hda3     /home     ext3     defaults,user_xattr     1 2

Now...I don't have /dev/hda3...

I have /dev/hda,hda1,hda2,hda5,hda6,hdc...so which one is it?

---

### Post by varunus on 2005-07-06
Just set up extended attributes for the partition(s) in your fstab that you want to be indexed.  So just open up your /etc/fstab, and add user_xattr to any line you want to be indexed.  I would suggest adding it to the lines that mount at '/' or at '/home'.

Enjoy.

---

### Post by gammyhand on 2005-07-06
[QUOTE=varunus]Just set up extended attributes for the partition(s) in your fstab that you want to be indexed.  So just open up your /etc/fstab, and add user_xattr to any line you want to be indexed.  I would suggest adding it to the lines that mount at '/' or at '/home'.

Enjoy.[/QUOTE]
 Thanks :)

---

### Post by gammyhand on 2005-07-06
I can search now but when I run beagled I get this error:

** (beagled:11964): WARNING **: _wapi_connect: Need to translate 2 [No such file or directory] into winsock error

Which means what?

Also - I thought I would be able to search for anything...I know full well I have an mp3 called "big in japan" but searching for "japan" brings up no results....do I need to reboot? I want beagled running automatically (is that wise?). Do I just add that command to startup items?

---

### Post by varunus on 2005-07-06
I've never seen the winsock error...maybe try a google search for it?  but if you can search, then I guess its ok...

Beagle will only index things in your home directory by default, you need to add "roots" to it for indexing.  Use the "beagle-config" utility to do this.  Also, it indexes slowly, so leaving it on overnight is the best way to go.

Adding beagled to your startup items works for me.

Have fun.

---

### Post by gammyhand on 2005-07-06
[QUOTE=varunus]I've never seen the winsock error...maybe try a google search for it?  but if you can search, then I guess its ok...

Beagle will only index things in your home directory by default, you need to add "roots" to it for indexing.  Use the "beagle-config" utility to do this.  Also, it indexes slowly, so leaving it on overnight is the best way to go.

Adding beagled to your startup items works for me.

Have fun.[/QUOTE]
 Hmm, well currently my music is stored inside my home directory. /home/ralph/music - so surely that should be indexed...or maybe I need to actually leave it indexing for more than 5 minutes ;)

---

### Post by gammyhand on 2005-07-06
[QUOTE=gammyhand]Hmm, well currently my music is stored inside my home directory. /home/ralph/music - so surely that should be indexed...or maybe I need to actually leave it indexing for more than 5 minutes ;)[/QUOTE]
 I can't find beagle-config....how do I get it? It is not in synaptic.

---

### Post by varunus on 2005-07-07
beagle-config should have come with the beagle package in synaptic.  Or maybe I'm spelling it wrong...just open up a terminal, type beagle and hit tab 3 times so all beagle commands will show up.  It should be there.

Yeah, I had to let mine index for 12 hours before I could really do any searches.

---

### Post by gammyhand on 2005-07-07
[QUOTE=varunus]beagle-config should have come with the beagle package in synaptic.  Or maybe I'm spelling it wrong...just open up a terminal, type beagle and hit tab 3 times so all beagle commands will show up.  It should be there.

Yeah, I had to let mine index for 12 hours before I could really do any searches.[/QUOTE]
 Cool - how do I know if it is actually indexing? I can't seem to see it doing anything, and how do I know it is finished so I can shut down? Or will it just resuming indexing when powered up again if beagled is in the startup list of programs?

---

### Post by varunus on 2005-07-07
Well, beagled has to be running for BEST to make a search.  So you should always keep it open, preferably in your startup programs.  It indexes in the background, and only does so when there's low CPU load.

To check the status, type "beagle-index-info" at a console.

---

### Post by gammyhand on 2005-07-07
[QUOTE=varunus]Well, beagled has to be running for BEST to make a search.  So you should always keep it open, preferably in your startup programs.  It indexes in the background, and only does so when there's low CPU load.

To check the status, type "beagle-index-info" at a console.[/QUOTE]
 thanks :) it is now indexing.

---

### Post by gammyhand on 2005-07-07
[QUOTE=gammyhand]thanks :) it is now indexing.[/QUOTE]
 What exactly in the results of beagle info tells me it is actually running?

ralph@ralph:~$ beagle-index-info Index information:

Name: Files
Count: 8

Name: IMLog
Count: 246

Name: Blam
Count: 0

Name: Liferea
Count: 0

Name: Mail
Count: 486

Name: Launcher
Count: 134

Name: Tomboy
Count: 0

Name: IndexingService
Count: 0

Name: Google
Count: -1

Name: EvolutionDataServer
Count: 0

Name: NetworkedBeagle
Count: -1

---

