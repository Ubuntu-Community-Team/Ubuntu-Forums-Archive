---
title: "CD burning fails with no apparent reason"
date: 2007-04-28
forum: General Help
---

### Post by anemon on 2007-04-28
Since I upgraded to Feisty, I can't seem to make Serpentine burn CD:s anymore. The process seems to start up all right, but in a short while I get a very uninformative error message:
```
Writing to disc failed
The writing operation has started. The disc may be unusable.
```

Running from terminal, I get this:
```
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/serpentine/recording.py", line 157, in __tick
    self.__prog.progress_fraction = self.__queue.progress
  File "/usr/lib/python2.5/site-packages/serpentine/operations.py", line 246, in __get_progress
    partial = self.__curr_oper.progress
  File "/usr/lib/python2.5/site-packages/serpentine/converting.py", line 304, in getProgress
    return self.__queue.progress
  File "/usr/lib/python2.5/site-packages/serpentine/operations.py", line 246, in __get_progress
    partial = self.__curr_oper.progress
  File "/usr/lib/python2.5/site-packages/serpentine/converting.py", line 51, in getProgress
    return self.__oper.progress
  File "/usr/lib/python2.5/site-packages/serpentine/audio.py", line 76, in <lambda>
    progress = property(lambda self: self._get_progress())
  File "/usr/lib/python2.5/site-packages/serpentine/audio.py", line 126, in _get_progress
    assert 0 <= self.__progress <= 1, self.__progress
AssertionError: 1.01198650712
```

Any ideas? Used to work like a breeze, but suddenly...

---

### Post by grimace on 2007-04-29
I have the same problem...what gives Serpentine!?

---

### Post by offchance on 2007-06-06
same here. repeatedly asks for a usable disc and then gives the error message above. multiple discs, multiple brands, etc. no go.

---

### Post by gm0neyl0ve on 2007-06-21
Same issue here. 

sigh. god forbid if I have to boot a winders box.

UPDATE. 
I just tried with gnomebaker and there were no problems.
I even used the disc from the failed attempt with Serpentine

---

### Post by Crafty Kisses on 2007-06-21
> **anemon said:**
> Since I upgraded to Feisty, I can't seem to make Serpentine burn CD:s anymore. The process seems to start up all right, but in a short while I get a very uninformative error message:
```
Writing to disc failed
The writing operation has started. The disc may be unusable.
```

Running from terminal, I get this:
```
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/serpentine/recording.py", line 157, in __tick
    self.__prog.progress_fraction = self.__queue.progress
  File "/usr/lib/python2.5/site-packages/serpentine/operations.py", line 246, in __get_progress
    partial = self.__curr_oper.progress
  File "/usr/lib/python2.5/site-packages/serpentine/converting.py", line 304, in getProgress
    return self.__queue.progress
  File "/usr/lib/python2.5/site-packages/serpentine/operations.py", line 246, in __get_progress
    partial = self.__curr_oper.progress
  File "/usr/lib/python2.5/site-packages/serpentine/converting.py", line 51, in getProgress
    return self.__oper.progress
  File "/usr/lib/python2.5/site-packages/serpentine/audio.py", line 76, in <lambda>
    progress = property(lambda self: self._get_progress())
  File "/usr/lib/python2.5/site-packages/serpentine/audio.py", line 126, in _get_progress
    assert 0 <= self.__progress <= 1, self.__progress
AssertionError: 1.01198650712
```

Any ideas? Used to work like a breeze, but suddenly...
You might want to try this program called "K3B" that might work.

---

