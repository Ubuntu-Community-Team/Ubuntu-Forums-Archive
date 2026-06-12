---
title: "Language Support Only in English"
date: 2007-08-09
forum: General Help
---

### Post by uechi on 2007-08-09
Hello all! New to the forums here (so sorry if I sound noobish or anything like that). 

Anyway, I'm having a problem. I want to enable multi-language UI support on my freshly installed Feisty 7.04, but I can't. On the live CD, there were tons of languages, but now that I go to install them via System->Administration->Language Support, nothing is listed but English. I can't install them via Synaptic or apt-get (the only language listed is English, apt-get says it can't find the package), nor can I choose a UI language other than English (which is what I want to do). Any advice is greatly appreciated.


EDIT: I figured out what the problem was. It turns out that I needed to update the package list by doing:

```
sudo apt-get update
```

That fixed my problem! Now I have all the languages listed, and I can also install other apps, like Blender and Audacity.

---

