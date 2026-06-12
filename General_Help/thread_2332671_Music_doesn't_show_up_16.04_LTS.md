---
title: "Music doesn't show up 16.04 LTS"
date: 2016-08-02
forum: General Help
---

### Post by wbmpertdsbcglobal on 2016-08-02
Music doesn't show up in Rhythmbox though it is shown in Music folder on desktop.
Looked through many posts on forum and can't find any help.

---

### Post by Geoffrey_Arndt on 2016-08-02
The program doesn't have an open file dialog? or scan the HDD to load the library???

---

### Post by wbmpertdsbcglobal on 2016-08-03
I don't know what you mean about open file dialog, but it scanned the HDD. The computer reports 'no music on the computer', even though there are tons of it in the music folder.
Perhaps it's the way I loaded the music into the folder (from a flash drive)?

I installed 16.04 LTS from a bought disc. 

Thanks for taking the time to help.

---

### Post by grahammechanical on 2016-08-03
Rhythmbox has a panel labeled "Select location containing music to add to your library." The default location is the Music folder. Click on the panel and we can browse to other locations. Even to other partitions.

Having selected a location we go to File>Add music and the music files should be listed in the main Rhythmbox panel. Click to import the tracks and the music files should be added to the library. Then click "Close" and you should be able to select a track to play.

What file format are these music files in? You may need to add a plugin or an audio codec.

Regards

---

### Post by wbmpertdsbcglobal on 2016-08-03
I did that and the files are shown, but are lightly shown and I cannot select them. Also, as I said before, the computer reports that there isn't any music on the computer. This I don't understand. By reporting this, I mean, this is what is reported when I select the music icon at the very bottom of the screen when the flash is selected.

---

### Post by wbmpertdsbcglobal on 2016-08-03
Still wrestling with this, but thanks to all who helped me.

---

### Post by Geoffrey_Arndt on 2016-08-05
The issue has zero to do with how you loaded the files in the music folder, but more to do with how the files are perceived by the operating system.     

What format are they (mp3) or something else?

In System Settings>Details>Default Applications . . . what music player is shown to be the default?

See this link for a very good (and short) tutorial of what to look for . . . to make sure your "file associations" are correct.
[URL="http://www.howtogeek.com/117709/how-to-change-your-default-applications-on-ubuntu-4-ways/"]
http://www.howtogeek.com/117709/how-to-change-your-default-applications-on-ubuntu-4-ways/[/URL]


BTW - - in most programs - if you go to the File option in the top menu (be sure the program is selected in Ubuntu as the active window) - - you should see the Open File(s) mechanism or dialog label.   That allows you to navigate to any folder to add music files (not all of my music files are in the music folder).

[SIZE=4]**EDIT**[/SIZE] . . . . was thinking about the actual cause of the "greyed out" files . . . . most likely you do not have the codecs installed.   So the system will not recognize mp3's as music files.   You can easily test that out by downloading a music file that is based on the .ogg format versus mp3.    The system, and consequently, the media player software will "see" those files and handle/play them properly.    To play mp3 files, go to Ubuntu Software and install the Synaptic  package manager. . . then open Synaptic and search for these two packages "ubuntu-restricted-addons" and "ubuntu-restricted-extras" and install them.    I think then you'll see your media players work as they are designed to.

---

### Post by wbmpertdsbcglobal on 2016-08-06
Installed music player with more codecs and problem solved. Many thanks to those who were patient with me and helped.

---

