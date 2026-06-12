---
title: "Intel 82801G sound broken"
date: 2007-05-22
forum: General Help
---

### Post by DonLorenzo on 2007-05-22
There are numerous posts in these forums about sound not working for this chipset. Reports of this go back to 6.06. Some colleagues who use Gentoo report success geting sound with the same chipset.

Alas, I'm not skilled enough to know what to do to get it to work like Gentoo. I am good enough to believe that the codebase is the same. The difference is likely to be in packaging. So, the question  is: ... is anyone from the Ubuntu Alsa driver packaging team working on this?

---

### Post by DonLorenzo on 2007-06-08
Following up to my own thread ...

I've solved the sound problem. What worked for me is this:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards)

OK, I had seen reference to the same kind of thing here, and had tried it. It did not work for me at that time. But... that was April 2007. It works now.

What's different?
I re-installed Ubuntu 7.04 several times since then. After almost every install the cumulative set of updates keeps getting larger and larger. That's the only thing that comes to mind, and no, I didn't look at each and every one of the updates to see if it was related.

Thus far, it works.

---

