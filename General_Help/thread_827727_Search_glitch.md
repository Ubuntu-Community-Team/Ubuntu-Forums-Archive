---
title: "Search glitch"
date: 2008-06-13
forum: General Help
---

### Post by teeleef on 2008-06-13
Hi all,   this is strange?   I have a music folder in a second drive containing sub-folders sorted by music type... pop, classical, rock etc.

I am using Hardy and have Beagle installed.  When searching using the search tool for example "Status Quo" all files are found relating to that band.  When I type 'Quo' the music files are again found, however when I type 'Status'............zilch!!! No audio files at all???? 

Is this a search indexing glitch or does my PC have a dislike for some of my tastes in music??? ;-)


Teeleef

---

### Post by dbera on 2008-06-13
> **teeleef said:**
> Hi all,   this is strange?   I have a music folder in a second drive containing sub-folders sorted by music type... pop, classical, rock etc.

I am using Hardy and have Beagle installed.  When searching using the search tool for example "Status Quo" all files are found relating to that band.  When I type 'Quo' the music files are again found, however when I type 'Status'............zilch!!! No audio files at all???? 

Is this a search indexing glitch or does my PC have a dislike for some of my tastes in music??? ;-)


Teeleef

Sounds like a bug. Can you do a quick test by doing
  $ beagle-query Status Quo
  $ beagle-query Status

The second should output all the ones in the first and more. And if possible can you paste a few lines which appear in the first but not in the second.

Edit: When you searched them in beagle-search were there other results as well ? Beagle returns the lastest 100 results by default so it could be that it found more than 100 other files matching "Status" so it did not return any music files. I think beagle-query shows the total number of files matched/returned which will give you an idea. You can also count the number of results from the output of beagle-query.

Try searching for "type:audio Status" to see if anything changes.

---

### Post by teeleef on 2008-06-13
OK dbera.....
This is a sample from the first search: -

file:///media/Music/MP3Files/Status Quo - Again And Again - 1978.mp3
file:///media/Music/MP3Files/Status Quo - Dear John.mp3
file:///media/Music/MP3Files/Status Quo - The Wanderer.mp3
file:///media/Music/MP3Files/status quo - backwater.mp3
file:///media/Music/MP3Files/status quo - big fat mama.mp3
file:///media/Music/MP3Files/status quo - break the rules.mp3
file:///media/Music/MP3Files/status quo - don't waste my time.mp3
file:///media/Music/MP3Files/Status Quo - Little Lady.mp3
file:///media/Music/MP3Files/status quo - i saw the light.mp3

and from the second.  No reference to the music files at all???

file:///usr/share/gnome/help/cpufreq-applet/nl/cpufreq-applet.xml
file:///usr/share/gnome/help/cpufreq-applet/nl/cpufreq-applet.xml%23cpufreq-applet-introduction
file:///usr/share/gnome/help/accessx-status/ca/accessx-status.xml
file:///usr/share/gnome/help/accessx-status/ca/accessx-status.xml%23accessx-applet-introduction
file:///usr/share/gnome/help/accessx-status/ca/accessx-status.xml%23accessx-status-interpreting
file:///usr/share/gnome/help/accessx-status/en_GB/accessx-status.xml
file:///usr/share/gnome/help/accessx-status/en_GB/accessx-status.xml%23accessx-applet-introduction
file:///usr/share/gnome/help/accessx-status/en_GB/accessx-status.xml%23accessx-status-interpreting
file:///usr/share/gnome/help/accessx-status/es/accessx-status.xml
file:///usr/share/gnome/help/accessx-status/es/accessx-status.xml%23accessx-applet-introduction
file:///usr/share/gnome/help/accessx-status/es/accessx-status.xml%23accessx-status-interpreting
file:///usr/share/gnome/help/accessx-status/it/accessx-status.xml


Typing status results in no audio files highlighted at all?

The same also goes for some other audio searches.   Mmmmmm


Teeleef

---

### Post by dbera on 2008-06-13
I think you facing "too many results" symptom here. And what if you try "beagle-query Status type:audio" ? or "beagle-query -source:documentation Status" ?

---

