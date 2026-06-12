---
title: "Music Player (Rhythmbox)"
date: 2005-08-12
forum: General Help
---

### Post by higherness on 2005-08-12
hello everyone, 

in windows you can change mp3 files "tags" so that when they are played, or important into windows media player the album, artist, etc will be shown. when importing my music collection into music player (rhythmbox), alot of the cds were messed up. example, 

the promise rings "30 degrees everywhere" was created 3 times, once with capitols, once with lowercase, and once more under "unknown".

is there anyway that i can open a folder with my music in it, tag all of the selected songs with the same album/artist? i dont mind doing through each cd and "tagging" them.

thank you, 

tommy.

---

### Post by mird on 2005-08-12
Try using something like [EasyTAG](http://easytag.sourceforge.net).  It takes a little bit of experimenting to figure out how it works, but you should find it very effective once you get a handle on it.  Read up on the documentation before you start. 

To install it, search for easytag in Synaptic or open up a terminal window and type: ```
sudo apt-get install easytag
```

---

### Post by higherness on 2005-08-12
thanks alot, 

ill let everyone know how it turned out.

---

### Post by higherness on 2005-08-13
thanks again, 

the program worked like a charm. it was everything i asked for. 

the kicker of the whole shebang is that i was up until 5AM. :-?

---

### Post by speedemonV12 on 2005-08-13
hey i tried to do what you said about how to get easy tag, and this is what happened

Reading package lists... Done
Building dependency tree... Done
Package easytag is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package easytag has no installation candidate


what do i do??

---

### Post by Donshyoku on 2005-08-14
Just an idea for the previous poster, simply because this helped me before...

Open your sources.list file by doing the following in the terminal:  sudo gedit /etc/apt/sources.list.

When it opens, look for the lines that should be the first repositories.  They should be marked after the url as restricted.  Delete everything after the url and add "universe" to the end of them.  That will open up a lot more repositories to you.

Now go into the terminal and type:  sudo apt-get update.

That should make sure that you have the new repositories enable and added to your Synaptic/apt-get listing.

Sorry I couldn't be more specific, I am stuck in Windows right now.  Hope that helps! :)

---

