---
title: "Using Mic as second headphone jack?"
date: 2008-04-07
forum: General Help
---

### Post by drafael on 2008-04-07
Well, I don't actually have a second pair of headphones with me at the moment, but it'd be interesting to know for future reference.. I did a quick google but no real leads so far. Mostly because I didn't know how to phrase it probably.

So, is it possible to have the same output signal through the headphone and mic jacks so that two pairs of headphones can be plugged in at once? If so, anyone got any links or such? Anyone managed it?

Cheers for any help in advance

---

### Post by xyphur on 2008-04-08
It would be wrong of me to assume that no soundcards can do this, as I'm quite sure it is possible, but generally speaking, your average run-of-the-mill standard audio hardware isn't capable of this. It's because typically each jack is hard-wired to a specific function of the audio hardware, and internally most audio decoder ICs just aren't equipped with the capability to alter what each jack is connected to in software.

It could probably be done at a driver level on some hardware that's physically capable of it, even though the original drivers didn't necessarily have it implemented, but that would require knowing what hardware can do it, and then writing the drivers for said hardware to incorporate this functionality.

Short answer: Nope, not possible. You could buy / make a splitter cable and that'd work sufficiently enough.

---

### Post by drafael on 2008-04-08
Well, I thought it'd be something like that but one can always hope =| Guess a splitter really is the only way..

Thanks for the help! ^^

---

