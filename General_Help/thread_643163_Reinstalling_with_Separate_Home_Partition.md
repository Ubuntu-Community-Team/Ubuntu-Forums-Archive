---
title: "Reinstalling with Separate Home Partition"
date: 2007-12-17
forum: General Help
---

### Post by Spektyr on 2007-12-17
I've got a machine that dual boots XP and Ubuntu that started out with Feisty and was upgraded to Gutsy.  Since the upgrade several annoying problems have surfaced.  I've chased them around and I'm tired.  I'm thinking of reaching for the Big Hammer.

What I want to know is this:  because I have Home on its own partition I know that I can reinstall without worrying about losing my data.  However, I want to know exactly what will be lost.

My thought is to first try a clean install of Gutsy.  Then, if the same problems are still there, go back to a clean install of Feisty.


But exactly what will the difference be?  Will I have to reinstall everything?  (Firefox extensions, desktop settings, so on and so forth.)


Or does having Home in it's own partition somehow make it so that I could reinstall and not notice any change at all?

Is there anything I need to know that I haven't asked about?  Anything specific to "downgrading" to Feisty?


Basically, I want to know how big a can of worms I'd be opening before I start something that can't be easily reversed.

---

### Post by lvleph on 2007-12-17
Everything but your settings will be lost. So mostly programs. But once they are installed they should be ready to go. Firefox extensions are all in the home directory, so those won't be lost. All bookmarks will also still be there. Just make sure you don't format the /home partition on reinstall.

Any drivers such as ndiswrapper will have to be redone. I am about to go back to feisty myself, but I am still trying to work things out.

---

