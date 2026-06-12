---
title: "supertux svn make error"
date: 2008-02-24
forum: General Help
---

### Post by Mal1024 on 2008-02-24
I'm trying to compile the SVN version of SuperTux. I've got as far as successfully running cmake, and now make gives several error codes:

[  9%] Built target squirrel
[  9%] Building CXX object CMakeFiles/supertux2.dir/src/main.o
In file included from /home/vbox/supertux/src/main.cpp:46:
/home/vbox/supertux/src/audio/sound_manager.hpp:27:20: error: AL/alc.h: No such file or directory
/home/vbox/supertux/src/audio/sound_manager.hpp:28:19: error: AL/al.h: No such file or directory
/home/vbox/supertux/src/audio/sound_manager.hpp:98: error: ‘ALuint’ does not name a type
/home/vbox/supertux/src/audio/sound_manager.hpp:99: error: ‘ALenum’ does not name a type
/home/vbox/supertux/src/audio/sound_manager.hpp:105: error: ISO C++ forbids declaration of ‘ALCdevice’ with no type
/home/vbox/supertux/src/audio/sound_manager.hpp:105: error: expected ‘;’ before ‘*’ token
/home/vbox/supertux/src/audio/sound_manager.hpp:106: error: ISO C++ forbids declaration of ‘ALCcontext’ with no type
/home/vbox/supertux/src/audio/sound_manager.hpp:106: error: expected ‘;’ before ‘*’ token
/home/vbox/supertux/src/audio/sound_manager.hpp:109: error: ‘ALuint’ was not declared in this scope
/home/vbox/supertux/src/audio/sound_manager.hpp:109: error: template argument 2 is invalid
/home/vbox/supertux/src/audio/sound_manager.hpp:109: error: template argument 4 is invalid
/home/vbox/supertux/src/audio/sound_manager.hpp: In member function ‘bool SoundManager::is_audio_enabled()’:
/home/vbox/supertux/src/audio/sound_manager.hpp:78: error: ‘device’ was not declared in this scope
/home/vbox/supertux/src/audio/sound_manager.hpp:78: error: ‘context’ was not declared in this scope
make[2]: *** [CMakeFiles/supertux2.dir/src/main.o] Error 1
make[1]: *** [CMakeFiles/supertux2.dir/all] Error 2
make: *** [all] Error 2

I can't find any documentation on either error codes. I'm a bit of a noob when it comes to compiling software.

---

### Post by pointone on 2008-02-24
Have you installed build-essential?

```
sudo apt-get install build-essential
```

---

### Post by Mal1024 on 2008-02-24
Turns out it wasn't installed. I thought I Had installed it a while ago :confused:

I still get the same error.
Any other ideas?

---

