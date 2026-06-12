---
title: "Uninstalling completely/MIDI help"
date: 2008-01-04
forum: General Help
---

### Post by Holonet on 2008-01-04
I usually do this via Synaptic Package Manager, under the option "mark for complete removal."  I've noticed as of late, that it does nothing of the sort.  If I select it, and try installing it again, it does so without downloading, meaning every program I've installed has the package still on my drive wasting space.

Plus, I've been trying to figure out how to use timidity to load a sf2 file for general midi, and there was no cfg file where the wiki said...so I tried installing timidity++ from the site, compiled manually, and then it didn't even play midis at all...so I tried complete removal, and I can still run timidity from the prompt...  Apparently "complete removal" means sort of if Ubuntu feels like it...anyone know how to combat this?

---

### Post by foolsh on 2008-01-05
no "remove completely" just removes the installed files and configurations
if you want to clean out the packages do a
 ```
sudo apt-get clean
```
timidity is an awkward beast at best you can use this guide 
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_MIDI_sound_server_.28Timidity.2B.2B.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_MIDI_sound_server_.28Timidity.2B.2B.29)
its for edgy but still works on any ubuntu release

---

