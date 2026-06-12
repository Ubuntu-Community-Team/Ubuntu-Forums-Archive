---
title: "need help building from source: no qt found"
date: 2007-09-16
forum: General Help
---

### Post by asafdav2 on 2007-09-16
i want to build museScore ([http://mscore.sourceforge.net/]("http://mscore.sourceforge.net/")) from source. one of the requirements is qt 4.3.0 or newer, so i downloaded the qt 4.3.1 source and built it. furthermore i made sure qmake is visible - 
```
export PATH=$PATH:/usr/local/Trolltech/Qt-4.3.1/bin/
```
however when trying to run 'make release' from musescore folder, i'm getting

CMake Error: Fatal error: QT (version >= 4.3.0) required.
Cmake tries to detect QT4 by searching for 'qmake' in your PATH
If you have QT4 installed, make sure qmake is found in your PATH.
-- Configuring done

any idea how to solve this?

---

### Post by wschweer on 2007-09-16
the new qt dir should be mentioned first in you new code:

export PATH=/usr/local/Trolltech/Qt-4.3.1/bin/:$PATH

---

