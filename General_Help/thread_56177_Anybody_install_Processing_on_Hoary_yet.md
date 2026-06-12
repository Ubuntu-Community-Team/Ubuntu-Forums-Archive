---
title: "Anybody install Processing on Hoary yet?"
date: 2005-08-11
forum: General Help
---

### Post by rherman on 2005-08-11
I've tried to get Processing going ([www.processing.org)](www.processing.org)), but when I click on their script it does nothing. On windows, this used to be my favorite playground for graphics/programming. Any help appreciated. I'm not a script person on ubuntu, but I suspect it has to do with the 'processing' script they've included. I'm also not too familiar with Jikes.

Thanks.

rob

---

### Post by rherman on 2005-08-11
Well, it was easier than I thought.

```
#!/bin/sh

CLASSPATH=$CLASSPATH:lib:lib/build:lib/pde.jar:lib/core.jar:lib/antlr.jar:lib/oro.jar:lib/registry.jar:lib/mrj.jar
export CLASSPATH


jikes -version 1> /dev/null 2> /dev/null
if [ $? == 0 ]
then 
  java processing.app.Base
else 
  echo
  echo It appears that the version of Jikes distributed with Processing
  echo cannot properly run on this system.
  echo 
  echo Possible solutions:
  echo
  echo + If you already have Jikes installed on your system, you may
  echo   just need to remove the version that is included with Processing.
  echo
  echo + You probably just need to track down a version of Jikes that will 
  echo   work with your distribution.
  echo 
  echo + You may need to install the rpm/package for compat-libstdc++
  echo   This is what it takes to get things running on most versions
  echo   of RedHat Linux or Fedora Core.
  echo 
  echo + If all else fails, or if you just like building stuff yourself,
  echo   you can download the source for Jikes from SourceForge:
  echo   http://sourceforge.net/project/showfiles.php?group_id=128803
  echo   And it just takes a simple ./configure and make, followed by
  echo   copying src/jikes to the processing-XXXX folder and you should 
  echo   be all set. 
  echo
  echo If you get stuck, ask questions online from the helpful folks via 
  echo the Processing discussion board: http://processing.org/discourse/
  echo
  echo Good luck!
fi
```

---

### Post by ulgor on 2008-05-22
ok... but which one of the solutions mentioned did you use?

For a fresh Hardy install, I did the following:

- download the jikes_1.22.tar
- extracted to home/downloads or /Desktop... whatever
- terminal: "cd jikes_1.22/./configure"
- ./configure didn't work, so I installed the g++ packages via Synaptics
- with g++, "./configure" worked fine
- then: "sudo make install"
- then I copied the jikes_1.22/src/jikes folder to my processing folder
- now I can start processing in the terminal via "sh processing"

..these steps are mentioned in the terminal when jikes fails to start, but as some users might try to solve this without knowing g++ etc. I thought I'd better post what I did.

hope that helps, good luck

---

