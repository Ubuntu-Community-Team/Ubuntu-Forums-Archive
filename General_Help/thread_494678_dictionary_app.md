---
title: "dictionary app"
date: 2007-07-07
forum: General Help
---

### Post by sailor.nir on 2007-07-07
I often look up words in the dictionary applet which I would later want to review in order to commit them to memory and improve my vocabulary. Is there an app which can help me do that?

---

### Post by linuxwizard on 2007-07-07
Not sure if this is what you are looking for 

[http://stardict.sourceforge.net/](http://stardict.sourceforge.net/)

---

### Post by sailor.nir on 2007-07-26
Ummm, I don't think so. I can't currently install anything, but from what I read, that's a cross-language dictionary app (very useful in itself). What I want is such an app where I can look up a word (in an English-English mostly, but also cross-lang), then "mark" it, and later be able to look through all my marked words. Creating my own dictionary may be an option, but would I be able to look up the definition in an existing dictionary and then just transfer the word with it's definition to that newly-created dictionary? If so, it would serve the purpose i seek.

---

### Post by nick_h on 2007-07-27
You can load an English dictionary into StarDict.  Then you can save selected words to a text file along with their definitions.

---

### Post by sailor.nir on 2007-08-08
Awsome app! Thank you! The downloaded (vs online) dictionary files and scanning in other apps is functionality I've been looking for.

As for the vocabulary training, I was ideally hoping for a list I could later traverse sequentially (or randomly), run a kind of quiz to match a word with its definition, etc. Anyone know of such app? Failing that, the text file does the job. Thanx again.

---

### Post by apetresc on 2007-08-08
If you're okay with running KDE apps, there's KVocTrain (KDE Vocabulary Trainer). For more info, see: [http://edu.kde.org/kvoctrain/index.php](http://edu.kde.org/kvoctrain/index.php)

To quote from the package, > Description: vocabulary trainer for KDE
 KVocTrain is a little utility to help you train your vocabulary when
 you are trying to learn a foreign language.  You can create your own
 database with the words you need.  It is intended as a replacement
 for index (flash) cards.
 .
 You probably remember flashcards from school.  The teacher would
 write the original expression on the front side of the card and the
 translation on the back.  Then look at the cards one after another.
 If you knew the translation, you could put it away.  If you failed,
 you put it back to try again.
 .
 KVocTrain is not intended to teach you grammar or other sophisticated
 things.  This is and probably will stay beyond the scope of this
 application.
 .
 This package is part of KDE, as a component of the KDE education module.
 See the 'kde' and 'kdeedu' packages for more information.


You can get it with ```
sudo apt-get install kvoctrain
``` However, if you don't have KDE installed, it's going to require a LOT of dependencies. I'm not aware of a similar thing to exist for Gnome, unfortunately :(

Anyway, hope this helps :)

---

