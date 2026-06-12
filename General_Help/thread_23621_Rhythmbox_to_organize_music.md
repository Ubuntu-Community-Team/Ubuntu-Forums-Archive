---
title: "Rhythmbox to organize music"
date: 2005-04-03
forum: General Help
---

### Post by bassMonkey on 2005-04-03
Hello, my first post here... 
Well, i've just moved to ubuntu and everything seems to work pretty great!

One small question tho, I like the ui of rhythmbox but I can't get it to organize my mp3 collection like iTunes on windows does. It asked me where I'd like my collection when I first ran it but it doesn't seem to copy anything there when I import new files... 

Thanks for making a great distro that is easy to use and setup!

---

### Post by Bo Rosén on 2005-04-03
I'm not sure if I understand you correctly, but Rhythmbox does not copy any files. What it does is import the location of all files from a directory and makes a list of them for it's own use.
Go to Music --> Import Folder (I'm using the Swedish version, but I imagine the menu options are close to that) and choose the folder where your mp3's are. This should make rhythmbox start indexing. This may take while if you have lots of files and a slow computer.

And welcome to Ubuntu!

Good Luck.

---

### Post by kosmic on 2005-04-03
Give a try to AMAROK.

sudo apt-get install amarok

---

### Post by Bo Rosén on 2005-04-03
[QUOTE=kosmic]Give a try to AMAROK.

sudo apt-get install amarok[/QUOTE]

Amarok is very cool, but it does need a few extra things to be installed... Like kde ;-)

---

### Post by bassMonkey on 2005-04-03
My bad, 

I misinterpreted the following: "Music library setup. Rhythmbox manages all of your music in a central music "library", so you can easily view, search, and organize it. In order to use this feature, you need to tell rhythmbox where to find your music. You may choose to skip this step; instead, you can add music to your library at any point later. Please choose one of the options below:"

I should've read it more closely, tought it would handle it like iTunes =/

I don't know about amarok, it doesn't seem to have very good iPod support? On the other hand I haven't tried out managing iPod with rhythmbox either but it does seem to play from it flawlessly.

Well, maybe I'll just give amarok a shot... Any good apps for organizing a large mp3 collection out there?

---

### Post by Buffalo Soldier on 2005-04-03
[QUOTE=bassMonkey]It asked me **where I'd like my collection** when I first ran it but it doesn't seem to copy anything there when I import new files... [/QUOTE]
 It does not ask you "*where you'd like your collection **to be***". But rather it asked "*where your collection **is***". There's a difference between those two.

I assume now you already have your Rhythmbox running. To add your collection to Rhythmbox **library** simply go to Music -> Import Folder. Browse to where your MP3 collection is and click open.

If you've manage to get that done. To add songs to certain **playlist** from the **library**:[list=1]
[*] Create a new list. Go to Music -> Playlist -> New Playlist
[*] Select files from Library. **CTRL + left click** or **SHIFT + hold and drag** to select multiple files.
[*] Drag to our newly created Playlist.
[*] Make sure the Playlist we want to save is highlighted.
[*] To save playlist: Go to Music -> Playlist -> Save to File
[/list]

If by any chance you have problem playing MP3 files. Enable the universe repository and **sudo apt-get update** and **sudo apt-get install gstreamer-plugins**.

EDIT: ooppss I guess I was too late. Took too long to answer your question. Sorry :p

---

### Post by GrayFox^ on 2005-04-30
Is there a way to get rhythmbox to scan your music folder for new/changed files on startup?? i get annoyed having to always go to import folder whenever i edit the id3 tags or change filenames etc. thanks

---

### Post by Professor X on 2005-04-30
> Is there a way to get rhythmbox to scan your music folder for new/changed files on startup?? i get annoyed having to always go to import folder whenever i edit the id3 tags or change filenames etc. thanks 

No.  Hopefully, the rhythmbox team will implement this feature in the next release.

---

