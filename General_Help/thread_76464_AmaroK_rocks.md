---
title: "AmaroK rocks"
date: 2005-10-15
forum: General Help
---

### Post by the_tiger on 2005-10-15
I love this program, it will display album covers, lyrics, biography in a nice interface within a single program. Annoyingly however it seems to have one flaw. When I move the position of the slider bar in a track the program closes instantly without any warning. Anyone else have this problem? Is there a solution.

Any other audio players offer the facilities of this program?

---

### Post by sbassett on 2005-10-15
[QUOTE=the_tiger]I love this program, it will display album covers, lyrics, biography in a nice interface within a single program. Annoyingly however it seems to have one flaw. When I move the position of the slider bar in a track the program closes instantly without any warning. Anyone else have this problem? Is there a solution.

Any other audio players offer the facilities of this program?[/QUOTE]
Have not had that problem yet. Though I do not use the supplied package for amarok. The first thing I did was build some debs for amarok (THE best music player) and k3b. I believe that amarok blows away it's iTunes competitor (it just needs ripping capabilities).

---

### Post by Lord Illidan on 2005-10-15
Can you load amarok from the terminal?
When it exits, copy the code from the terminal..here.

---

### Post by Dr. Nick on 2005-10-15
I had a similar problem with it yesterday, resizing the windows inside would lock the computer. I switched to quod libet, here is my thread which has a discussion of alternate players. [http://ubuntuforums.org/showthread.php?t=76142](http://ubuntuforums.org/showthread.php?t=76142)
quod libet will do alot of that same stuff like lyrics and cover art with plugins, the problem with its cover art though is each album must be in a seperate folder since it doesnt have a database like amaroK, so if you have a single folder with all of your music album covers will be hard to set up.

---

### Post by the_tiger on 2005-10-19
I tried running Amarok in the terminal but did not get any output twice when it crashed. Bizarely I was mucking about in the terminal another time and happened to move the slider. This time I got an output. Here it is:

At startup

amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
DCOP Cleaning up dead connections.
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow

on crashing

X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3200037

Any ideas people?

For the record I am running breezy with gnome.

---

### Post by the_tiger on 2005-10-19
Hmm,

just encountered another error

If I click on the album cover (already downloaded) it gives me the error in a window:

Could not launch the browser

Could not find service 'kfmclient'

---

### Post by Dr. Nick on 2005-10-19
[QUOTE=the_tiger]Hmm,

just encountered another error

If I click on the album cover (already downloaded) it gives me the error in a window:

Could not launch the browser

Could not find service 'kfmclient'[/QUOTE]

Do you have konqueror installed, I think kfmclient is part of conqueror , it may be like a web link or something, I am going to compile the CVS version of amaroK now and see if I have alot of problems

---

### Post by the_tiger on 2006-05-09
Would now highly recommend Listen as a music player in gnome. It has similar features to Amarok.

---

### Post by JoeMetal on 2006-05-09
AmaroK would never work for me in Gnome so I started using Listen and I'm never going back. :)

---

### Post by pillypoon on 2006-05-09
[QUOTE=the_tiger]I love this program, it will display album covers, lyrics, biography in a nice interface within a single program. Annoyingly however it seems to have one flaw. When I move the position of the slider bar in a track the program closes instantly without any warning. Anyone else have this problem? Is there a solution.
[/QUOTE]


You can try building Amarok from SVN source.  I had a few problems with the Amarok from the repos.. I tried the SVN and it works perfectly with Gnome and KDE.  Use the following how-to written by mlomker:
[http://www.ubuntuforums.org/showthread.php?t=80492](http://www.ubuntuforums.org/showthread.php?t=80492)  

Pilly

---

### Post by seatea on 2006-05-09
I started using Amarok lately. I basically like the way it is laid out and have not had any problems. The one thing I wish it would not do is  flash a small blue window every time it  changes tracks  or an adjustment is made. Is there a way to get it to stop doing that. I find that behavior annoying.

---

### Post by pillypoon on 2006-05-09
[QUOTE=seatea]I started using Amarok lately. I basically like the way it is laid out and have not had any problems. The one thing I wish it would not do is  flash a small blue window every time it  changes tracks  or an adjustment is made. Is there a way to get it to stop doing that. I find that behavior annoying.[/QUOTE]

I think what you are refering to is the OSD.  Refer to this link for help..  [http://docs.kde.org/development/en/extragear-multimedia/amarok/configure-osd.html](http://docs.kde.org/development/en/extragear-multimedia/amarok/configure-osd.html)

Pilly

---

### Post by mrazster on 2006-05-09
I was also having small problems/bugs with amaork from the repos....but after installing it from SVN...everything works perfect for me. Stable as hell....no problems what so ever.
I absolutely love this player...!!!

---

### Post by seatea on 2006-05-09
Thanks. I can't believe I overlooked that part of the settings. I think when I looked through the settings the first time, I thought  that OSD referred to the whole gui. I had even tried a google search and looked through the config editor for a way to stop the pop-ups! Duh.

---

