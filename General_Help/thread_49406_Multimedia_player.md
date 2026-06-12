---
title: "Multimedia player"
date: 2005-07-16
forum: General Help
---

### Post by lotech on 2005-07-16
How do I play DVD or VCD ? when I start the movie player I got an error that the decoder is not installed, but what decoder and how to install ? and I can't find a player that support midi and mp3, I follow the default install to setup Ubuntu, am I missing something ?

---

### Post by Whtbflo on 2005-07-16
You are probably missing the codecs which you can get by following the instructions here: [http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

---

### Post by retsel on 2005-08-09
I have the same problems. I've been trying for weeks now to jump through all of the hoops that are apparently necessary to be able to view a DVD movie, and I'm still unable to do it. Also, I need to be able to play simple midi files, and cannot find a midi player that I can get to work in Kubuntu. These are trivial things to do in Windows, but in Kubuntu (and I assume in Linux in general) they are apparently very difficult problems. In both cases there seems to be particular pieces of the puzzle that are not included in the packages that are downloaded by Synaptic. And, while I really appreciate the suggestions that have been made on the forum, if they've done any good I can't tell it from the results.

---

### Post by varunus on 2005-08-09
Here's how to get MIDI in Ubuntu:
[https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo](https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo)

---

### Post by retsel on 2005-08-10
Thanks for the link! I just did the basic steps outlined in the article, and the resulting quality of the midi sound was not great, but it was sufficient for my need. Know any good links for the DVD movie viewing problem?

---

### Post by blu.gecko on 2005-08-10
in linux the best dvd player so far that I have found is vlc, check out the website at videolan.org, they make a windows version aswell, they support all the codecs in the package, so installing others might screw things up, to install this program open xterm and type 

sudo apt-get install vlc

or goto system/admin/synaptic and search GVLC and install.

POST RESULTS

---

### Post by retsel on 2005-08-10
Gvlc is now called wxvlc. I've tried and tried to get it to work, and I can't do it. I can't figure out what's wrong. Wxvlc comes up, but when I tell it to open the DVD it puts something up on the screen for a millisecond - no sound - then nothing.

---

### Post by blu.gecko on 2005-08-10
I did a update on mine, I typed in "sudo apt-get install VLC" and it said you currently have uptodate vlc, if you look it up in symantec its labeled VLC, its the GTK ver.

Try this:
sudo gedit /etc/apt/sources.list

look for a line near the top like

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main

and change it to

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

(and the next one as well - you get the idea)
this adds the universe, restricted and multiverse file repositories

vlc is in universe

save and then
sudo apt-get update
sudo apt-get install vlc

---

### Post by varunus on 2005-08-11
[QUOTE=retsel]Thanks for the link! I just did the basic steps outlined in the article, and the resulting quality of the midi sound was not great, but it was sufficient for my need. Know any good links for the DVD movie viewing problem?[/QUOTE]

Sound quality can be improved by using a better soundfont.  The default one included with timidity/ubuntu isn't that good.  There are instructions on that page.

---

