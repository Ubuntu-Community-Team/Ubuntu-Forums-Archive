---
title: "General question"
date: 2007-04-05
forum: General Help
---

### Post by sambones on 2007-04-05
Very easy question I'm sure for most of you, but being new to Ubuntu, I don't know how to designate a default audio player for downloaded tunes from amule. I then want to export songs from amule to the player, but I'm at a loss as to where to find the folder for amule songs. I've tried all kinds of searches to no avail. Thanks for any help.

---

### Post by cantormath on 2007-04-05
To associate a file type (ie: mp3) you can right click on the file and click the open with tab.  Select the program you want to open it with.

I dont use amule so I dont know where it puts the music.  You could open Rhythmbox and have it search the / drive (which is the entire drive) for media.  

A more productive way of finding your music would be by typing this into terminal:
```
:~$ sudo find / -name *.mp3

```

Most players will let you load music into the players database for furture reference.

---

### Post by crispy_420 on 2007-04-05
Have not used this but I do have it installed so I ran it. If you go the "Preferences" it will open a new window of settings. In there is the option of directories, by default it looks as though it runs from a hidden directory in you home folder. And you can change it to you choosing. If you want to get to it, go to your home folder and hit crtl + h to view hidden folders.

As far a playing the audio, I'm not familar. Does it play within the app or does it use a default player from Ubuntu? If default you can always select a similar file type and right click, select properties. Then a new window will a appear, selcet the tab "Open With" and choose a player. If the player you want is not there choose add. Then you get an alphabetical list to pick installed player.

Hope that helps.

---

### Post by ispmarin on 2007-04-05
The aMule puts all downloaded stuff in a folder called .amule. Note the `dot` before the name: on *nix systems, it denotes a hidden file/directory. To see this hidden files/directories, go to nautilus -> see -> hidden files. 

Inside .amule you will find the folder Incoming - this is where the downloaded files are. You can set a default audioplayer to a kind of file (mp3, mpg, avi, etc) right-clicking on the file, selecting Open With, and selecting the player that you like.

 If you did not installed any player, try to install using synaptic: system -> administration -> package manager (synaptic). I like very much xmms and amarok. 

The site [http://ubuntuguide.org/wiki/Ubuntu_dapper]("http://ubuntuguide.org/wiki/Ubuntu_dapper") can help you a lot.

Hope it helps!

---

### Post by sambones on 2007-04-06
Thank you very much for your replies. You all were absolutely right! One can choose an audio player in amule in the 'preferences' section. and going to home folder and pressing control/h gets the incoming music folder for amule. Brilliant! Makes it easy as eating pie. Thanks again.

---

### Post by crispy_420 on 2007-04-06
no problem

---

