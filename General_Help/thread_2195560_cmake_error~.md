---
title: "cmake error~"
date: 2013-12-24
forum: General Help
---

### Post by cymssss45 on 2013-12-24
when i press c to configure
there are some errors
so what can i do to solve it??

 CMake Error at
 /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:91
 (MESSAGE):
   Could NOT find Gettext (missing: GETTEXT_MSGMERGE_EXECUTABLE
   GETTEXT_MSGFMT_EXECUTABLE) (Required is at least version "0.15")
 Call Stack (most recent call first):
   /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:252
 (_FPHSA_FAILURE_MESSAGE)
   /usr/share/cmake-2.8/Modules/FindGettext.cmake:46
 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
   CMakeLists.txt:21 (find_package)

---

### Post by monkeybrain20122 on 2013-12-24
It says you need to install gettext, it is in the repo.

---

