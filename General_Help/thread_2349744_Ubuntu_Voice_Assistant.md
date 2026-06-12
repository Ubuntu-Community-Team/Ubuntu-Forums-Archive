---
title: "Ubuntu Voice Assistant"
date: 2017-01-17
forum: General Help
---

### Post by alexwaltz on 2017-01-17
Google has Ok Google, Apple has Siri, Amazon has Alexa, does Ubuntu have something that we can use to create our own Ubuntu personal assistant?

Thank you

---

### Post by howefield on 2017-01-18
[Lucida]("https://github.com/claritylab/lucida") ?

Formerly sirius..

---

### Post by dragonfly41 on 2017-01-18
Personal assistant in what subject domains?

---

### Post by alexwaltz on 2017-01-18
> **dragonfly41 said:**
> Personal assistant in what subject domains?


It would be nice to just be able to do voice searches in Google Chrome without having to use the mouse to click on icons to activate voice search.

---

### Post by ian-weisser on 2017-01-18
Ubuntu is community-driven.
If you want that feature, then gather a few friends, figure out how to put the pieces together, broadcast the result, and (if needed) package or Snap the solution.

---

### Post by dragonfly41 on 2017-01-18
I have not tried this but searching around there is Simon in Ubuntu repo.

[https://www.maketecheasier.com/simon-linux-speech-recognition/](https://www.maketecheasier.com/simon-linux-speech-recognition/)

Simon is claimed to be similar to Siri so it is a good start for an experiment.

You would need to define some control words and have your speech-to-text stream constantly scanned.

Then from a control command API trigger a bash script to run your speech-to-text search in Chromium.

...

I thought from your opening question that you were searching for something more complex like IBM Watson.
See IBM Bluemix site.

i.e. a personal assistant to scan through a corpus of many thousands of documents in a subject domain.

That is what I'm looking for .. open source Watson alternative.

Your requirement is somewhat simpler than ai based engines.

---

### Post by ian-weisser on 2017-01-18
Future-voice-command was one of the original reasons for developing Ubuntu HUD.
HUD is that 'type your command' box that appears when you hit the 'alt' key. Unity only.
It makes application menus, options, and commands accessible in a standard way. Once voice recognition has figured out a word, and identified it as a command, it can simply feed that command to HUD to accomplish the action.

EDIT: 'HUD', not 'HUB'

---

### Post by SuperFreak on 2017-01-19
> **ian-weisser said:**
> Future-voice-command was one of the original reasons for developing Ubuntu HUB.
HUB is that 'type your command' box that appears when you hit the 'alt' key. Unity only.
It makes application menus, options, and commands accessible in a standard way. Once voice recognition has figured out a word, and identified it as a command, it can simply feed that command to HUB to accomplish the action.


I believe it is Ubuntu HUD for Heads Up Display

---

### Post by ian-weisser on 2017-01-19
Thanks. Fixed.

---

