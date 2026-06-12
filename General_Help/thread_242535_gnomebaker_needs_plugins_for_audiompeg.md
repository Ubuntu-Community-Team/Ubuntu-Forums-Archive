---
title: "gnomebaker needs plugins for audio/mpeg"
date: 2006-08-23
forum: General Help
---

### Post by cptjaben on 2006-08-23
When I try to burn an audio cd in gnomebaker, it says that it needs plugins for audio/mpeg's. does anyone know what plugins are needed? and if so where one can find/install them. Thanks

---

### Post by DCM36 on 2006-08-24
I'm guessing you are probably trying to burn an audio cd with mp3 files. I think that if you do this:
```
sudo apt-get install libmad0 libsmpeg0
```
should install the needed decoders.

If you get a can not find package error, you need to enable the universe repository. For some easy to follow instructions to do this, look [here]("http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29").
I beleive that this is correct, but if not, please correct me.

---

### Post by cptjaben on 2006-08-24
Thanks for the help, that seemed to fix the problem.

---

### Post by babis85 on 2006-09-04
I have exactly the same problem and those libs were installed.
What should i do?
Thanks.

---

