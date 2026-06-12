---
title: "Can't play certain flac files in Amarok"
date: 2007-03-12
forum: General Help
---

### Post by btboudreaux on 2007-03-12
I can't seem to play certain types of flac files in Amarok. These same files play fine in other players, but in Amarok it just won't play.

After reading some things, I think it has to do with certain files having some kind of tags that freeze up the player and make it crap out. I read that libxine1.1.2 is the source of the problem and it is fixed in libxine1.1.3.

My question, is there any way to upgrade libxine without upgrading my whole system to feisty? I already tried upgrading to Feisty and it hosed my system. (I restored from a backup image). I also tried upgrading just libxine by changing my sources to feisty but then it completely hosed Amarok and I couldnt play any file.

Anyone have another solution or can help me out or experienced this same thing?

---

### Post by musicinmybrain on 2007-05-11
There was a problem with libxine1.1.1 that required a patch. libxine1.1.2 should be okay. Do you have libxine1-plugins (or libxine-extracodecs... don't remember which one is available in Edgy) installed?

---

