---
title: "AOL Game Not Working- Flash Problem?"
date: 2016-09-09
forum: General Help
---

### Post by sasafrass452 on 2016-09-09
I wanted to play a bingo game on the aol website, but the game doesn't load. I have the freshplayer plugin installed, but all I get is a black square on the website. What can I do to make this work?

---

### Post by ajgreeny on 2016-09-09
It would help to have a link for the game's web-site to check what is needed but missing in your case.

---

### Post by sasafrass452 on 2016-09-09
My appologies.... Here's the link: [http://www.aol.com/games/play/masque-publishing/bingo-blackout/](http://www.aol.com/games/play/masque-publishing/bingo-blackout/)

> **ajgreeny said:**
> It would help to have a link for the game's web-site to check what is needed but missing in your case.

---

### Post by Dennis N on 2016-09-09
Tried your link with varying results. For me, the game doesn't run with Xubuntu 16.04, either using Firefox or Chromium. Firefox uses 11.2.202.632; Chromium uses 22.0.0.209. The game _does_ run in Manjaro Linux using Chromium, flash player 22.0.0.209 (but not with Firefox and flash 11.2.202.632). Something about Manjaro's Chromium allows it to run. 

Same behavior has been seen before with flash content:

[https://ubuntuforums.org/showthread.php?t=2319957](https://ubuntuforums.org/showthread.php?t=2319957)

Note post #7, where I reported it worked in Manjaro Chromium only, and the following posts. No ultimate solutions there.

---

### Post by oldos2er on 2016-09-09
It worked for me on Chrome 53.0.2785.101 (64-bit); didn't work on Firefox 49.0b10, got an error that it couldn't find flash.

---

### Post by ajgreeny on 2016-09-10
And I got this error in both FF and chromium, even though I am running the most recent flash plugin, 22.0.0.209, in both browsers.
> We have detected that you don't have the required plugin to load the game.

Get Flash Player

---

### Post by Dennis N on 2016-09-10
And I can report "Bingo Blackout" runs in Korora (Fedora) Chromium (version 52 with flash 22.0.0.209).

---

### Post by pqwoerituytrueiwoq on 2016-09-10
Using firefox and chrome i got the same error ajgreeny did
however using flash 23,0,0,162 ( [http://labs.adobe.com/downloads/flashplayer.html](http://labs.adobe.com/downloads/flashplayer.html) ) in firefox i managed to get a black square
(Edit: using a clean firefox profile and flash 23,0,0,162 it runs, id guess that game needs 3ed party cookies to run)

Adobe now plans to update NAPI flash on linux
* [http://www.omgubuntu.co.uk/2016/09/adobe-announced-will-restart-support-flash-linux](http://www.omgubuntu.co.uk/2016/09/adobe-announced-will-restart-support-flash-linux)

---

### Post by sasafrass452 on 2016-09-11
WOW, that's awesome!!! The article states that chrome has the latest version built in, so thumbs up to google.... BTW, I just installed chrome, & can happily confirm that the bingo game works!!! I haven't quite decided to switch browsers yet, but I'm getting there....

> **pqwoerituytrueiwoq said:**
> Using firefox and chrome i got the same error ajgreeny did
however using flash 23,0,0,162 ( [http://labs.adobe.com/downloads/flashplayer.html](http://labs.adobe.com/downloads/flashplayer.html) ) in firefox i managed to get a black square
(Edit: using a clean firefox profile and flash 23,0,0,162 it runs, id guess that game needs 3ed party cookies to run)

Adobe now plans to update NAPI flash on linux
* [http://www.omgubuntu.co.uk/2016/09/adobe-announced-will-restart-support-flash-linux](http://www.omgubuntu.co.uk/2016/09/adobe-announced-will-restart-support-flash-linux)

---

