---
title: "[SOLVED] Synaptic recomends software that it conflicts with?"
date: 2007-08-11
forum: General Help
---

### Post by evolving_monkey on 2007-08-11
I've noticed this a few times. Thought it seemed worth asking about

With a few of the programs I've looked at some of the software under "recommended" is also listed as something it conflicts with under "dependencies".

Here is an example. I was looking at xchat. This package  recommends esound-clients. I searched for esound-clients with Synaptic to check it out. It says it conflicts with libesd-alsa0.   I then looked up libesd-alsa0. It had esound-clients under recommended as well as listed as a conflict under dependencies.

I assume it is accurately listed as a conflict and not as recommended. That was the result of my previous experiences.

Is this just a glitch or am I missing something.

Thanks for your time.

---

### Post by yabbadabbadont on 2007-08-11
Usually there is a version requirement in the conflicts section.  As far as I have seen, the package that is recommended is newer than the version that conflicts.

---

### Post by evolving_monkey on 2007-08-11
I see your point. That answers the question on that one. Another one I was looking at was a similar situation with nvidia-settings. On that one the software version numbers aren't included with everything that is mentioned under dependencies. I did actually run into conflict issues with nvidia-settings and nvidia-glx with an install on another test system I loaded Ubuntu on. It did have have an older nvidia card in it so it might have used an older driver which might explain that problem.

It's not a big deal. Most of the time I run into trouble it's because of "user error" anyway.  I'll give it a shot and see what happens.

Thanks.

---

