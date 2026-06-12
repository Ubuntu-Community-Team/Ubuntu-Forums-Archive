---
title: "*.WMV in Totem"
date: 2005-08-30
forum: General Help
---

### Post by ubuntuubuntu on 2005-08-30
What should I do for Totem to be able to play .wmv files?
Please explain me step-by-step.
Thanks!

---

### Post by DJ_Max on 2005-08-30
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by ubuntuubuntu on 2005-08-30
I'm sorry, but it wasn't enough for me. Could you be more specific? 
Thanks a lot!

---

### Post by d1337 on 2005-08-30
I can't tell if you were joking or not.  The second post in DJ_Max reply was to the unofficial Ubuntu guide which should be the starting place for practically every install for a desktop environment.  If you follow the instructions from where he linked, you should be viewing .wmv's in a short while if you have a decent connection.  My suggestion, though, would be to take a bit of time and start from the top instead of where he linked it...but that's just me.  You'd be surprised of what you might learn...not to mention the functionality of Ubuntu with some very simple apt-get and copy paste.

---

### Post by NeoChaosX on 2005-08-30
Since he wants specific, let's just get to the the point.

Open up a terminal, and type in this command:

**sudo apt-get install totem-xine w32codecs**

There you go, Totem can now play WMVs.

---

### Post by woedend on 2005-08-31
[QUOTE=NeoChaosX]Since he wants specific, let's just get to the the point.

Open up a terminal, and type in this command:

**sudo apt-get install totem-xine w32codecs**

There you go, Totem can now play WMVs.[/QUOTE]
 lol...and this will not work and bring up new questions(the w32 repo would not be enabled). Read the entire ubuntu guide.  This is not to be snobbish and not because we do not want to help you, its just that its a MUST for beginners(helped me tons) and will answer 90% of the questions you will post here.  and failure to do so is sheer laziness.

---

### Post by WebbyBabe on 2005-08-31
How can I play embedded WMV files from launch.com? Has anyone gotten that too work?

---

### Post by arnieboy on 2005-08-31
[QUOTE=WebbyBabe]How can I play embedded WMV files from launch.com? Has anyone gotten that too work?[/QUOTE]
read this post of mine and u will be able to play launchcast videos on firefox:
[http://ubuntuforums.org/showpost.php?p=259109&postcount=27](http://ubuntuforums.org/showpost.php?p=259109&postcount=27)

---

### Post by ubuntuubuntu on 2005-09-02
When I type "sudo apt-get install totem-xine w32codecs", I get the following messages:
Reading package lists... Done
Building dependency tree... Done
Package totem-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package totem-xine has no installation candidate

What should I do?

---

### Post by az on 2005-09-02
Just use synaptic for installing stuff.  It is easy to enable extra repositories and so forth.  The, just search for the packages you want and off you go.

Offhand, I do not know which repository has the w32codecs.

I would not reccommend Mplayer.  Totem does a much better job.  You can install the mediaconnectivity firefox extention which allows you to view stuff in totem.

---

### Post by az on 2005-09-02
"To use some multimedia codecs/plugins, you will need to use the Hoary-extras repository. To use this, in the Synaptic repositories dialog box, click Add and then Custom. In the dialog box, type in the following APT line: 

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
"

---

