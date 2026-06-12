---
title: "Howto: Watch multiple folders in Rhythmbox"
date: 2007-08-05
forum: General Help
---

### Post by atselby on 2007-08-05
I needed this earlier, I've got a few folders for music, and discovered this on IRC thanks to xtKnight and thought I should post it.

So lets say you have more than one folder of music for some reason and want to play it all through Rhythmbox, but it only lets you select one folder to watch. What do you do? Well you can create symbolic links, right click "make link", of the other folders and put them in one folder to be watched by Rhythmbox. For example lets say I have one folder called "music" where you rip all your music to, and another for any single songs you've bought or otherwise come across, and you dont want to put those into the music folder. Instead its in music2 or something. So you can create a symbolic link to music 2 in your home directory, and move the link to music. Then go to Rhythmbox, edit, preferences, library, and set the folder to watch as music, or wherever you put the link for the other folder into, and click watch for new files. 

Bam, you can now keep your files in the locations they're in, seperated, but see them all in Rhythmbox. If theres another easier way to do this, that'd be cool too.

---

### Post by frodon on 2007-08-06
This is strange i have Rhythmbox and my music is in 2 folders and Rhythmbox allows me to listen the music in both directories.
I just add all the forlders i need using the Rhythmbox menu.

What is your Rhythmbox version ?

---

### Post by atselby on 2007-08-06
0.10.0, installed from the repositories two days ago. It might exist, but if so I couldn't find it, nor could anone I asked... Looks like .10 is the latest... Odd, if it does exist be default for you, was it removed?

---

### Post by frodon on 2007-08-06
I have the same version. Are you really not able to add more than one directory using the main menu and clicking "import a folder" ?

---

### Post by atselby on 2007-08-06
No, I can do that, but I wanted to have it set ot watch two folders, and not have to manually import new songs from a folder. Or does it do that and I missed it?

---

### Post by frodon on 2007-08-07
It is how i use it i have 2 folder which contain my music so i imported the 2 folders and all the music is in the rythmbox base.
However in preference you can choice a folder where rytmbox will mook automatically for new songs and indeed here you can only chose one folder so for this feature your workaround seems the only way to use 2 folders.

---

### Post by doclivingston on 2007-08-07
You can actually have Rhythmbox watch more than old folder - it's just not currently exposed in the UI, which means you need to use gconf-editor (Tools->Configuration Editor) to set it up. In case anyone wants to play with it, the gconf key /apps/rhythmbox/library_locations is a list and you can add more than one item to it. The first one listed is what gets used if you rip CDs.

---

### Post by atselby on 2007-08-07
I hadn't messed with looking around in Gconf for this, didn't know that existed doclivingston.

---

### Post by Endolith on 2007-11-30
> **doclivingston said:**
> You can actually have Rhythmbox watch more than old folder - it's just not currently exposed in the UI

That's incredibly lame.  How did you find out about that?

---

