---
title: "How to convert multiple files using tovid?"
date: 2006-12-15
forum: General Help
---

### Post by Nasso on 2006-12-15
Hi all!
I just tried out tovid and its wonderful :) Have tried the gui before but decided to use the terminal this time, so much better. Never got that gui thing working but the terminal was sooooo easy! :)

I have a problem though. Tovid wont take two video files as input. I have a movie that is split into two files that i want to convert to one dvd. Tried this;

```

tovid -pal -full -dvd -in /path_to_files/file.cd*.avi -out finished_movie

```

Tovid complains about the parameter to -in.

Can i "stick" those two videos together in any simple way or can i just convert each of them and merge the isos somehow?

Which method is fastest? I dont want to wait a whole lot of time. Putting two videofiles together and reencode the whould take alot of time i guess and then i probably have to mess around with video and audio settings. Dont want that, thats why i use tovid :)

EDIT: Ooops, made a huge mistake :) It did take that command i wrote here, just wrote it wrong in the terminal ;) Dont know if it will just make two mpegs och will put it together in one file. Will tell you in a couple of hours :)

Edit2: It only converted the first movie :(

Edit3: Fixed this myself, hopefully. By running tovidgui and creating a menu with 2 videos and then clicking the encode button you can see the commands that will be executed. Just to modify them to fit your needs.

---

### Post by binks on 2006-12-15
hi if you install tovid from svn you can use the new testing gui which is better 
run it after installing svn version by running the cmd **tktodisc**

;) binks

---

### Post by Nasso on 2006-12-16
This is the commands i ended up using. Complete and sexy as hell! :) From start to end. From avi or whatever to iso. See this as a mini-tutorial.

Automatic menu:
todisc -pal -dvd -menu-title "Titel" -files file1.mpg file2.mpg -titles "Titel 1" "Titel 2" -out /tmp/dvdfolder/
mkisofs -dvd-video -o dvd.iso /tmp/dvdfolder/"

simple meny:
tovid -pal -dvd -full -in "/path/file1.avi" -out "/tmp/file1"
tovid -pal -dvd -full -in "/path/file2.avi" -out "/tmp/file2"
makemenu -pal -dvd "text video1" "text video2" -out "/tmp/menu"
makexml -dvd -menu "/tmp/menu.mpg" "/tmp/file1.mpg" "/tmp/file2.mpg" -out "/tmp/disc"
dvdauthor -x disc.xml
mkisofs -dvd-video -o dvd.iso /tmp/disc" 

Should be correct :)

---

