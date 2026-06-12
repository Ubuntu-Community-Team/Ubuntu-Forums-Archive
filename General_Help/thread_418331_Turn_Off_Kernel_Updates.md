---
title: "Turn Off Kernel Updates"
date: 2007-04-22
forum: General Help
---

### Post by daynah on 2007-04-22
My dad has a Creative X-Fi. After much searching it seems the only way to get *some* sound is  what I've found in this guide [here,]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+X-Fi.&chip=UNKNOWN&module=emu10k1") which is compiling a kernel. I don't want to do this if one day dad is going to use the update manager, get a kernel update, and then whine about how Ubuntu broke.

So, how can I disable kernel updates until I have a free day to recompile?

---

### Post by cantormath on 2007-04-22
> **daynah said:**
> My dad has a Creative X-Fi. After much searching it seems the only way to get *some* sound is  what I've found in this guide [here,]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+X-Fi.&chip=UNKNOWN&module=emu10k1") which is compiling a kernel. I don't want to do this if one day dad is going to use the update manager, get a kernel update, and then whine about how Ubuntu broke.

So, how can I disable kernel updates until I have a free day to recompile?

could shut off the update manager altogether and ssh into the box and update yorself. This is what I do for my parents.

---

### Post by tom56 on 2007-04-22
There's an option in Synaptic somewhere - I think you need to find the package then go to Package -> Freeze or Hold or Lock of something like that.

---

