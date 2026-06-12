---
title: "How to Compile this QQ Plugin for Pidgin Tarball?"
date: 2014-08-28
forum: General Help
---

### Post by mastercosgrove on 2014-08-28
So I've recently switched from Windows onto Ubuntu. However, there are still somethings I cannot access with Ubuntu I could with Windows. One of which is my QQ IM client. I found there is a plugin, but this is my first attempt to compile something from source code and I just confused as I cannot make it install properly.

[https://github.com/xiehuc/pidgin-lwqq](https://github.com/xiehuc/pidgin-lwqq)

^---------------

I download the tar.gz file locate here: [https://github.com/xiehuc/pidgin-lwqq/archive/v0.4.0.tar.gz](https://github.com/xiehuc/pidgin-lwqq/archive/v0.4.0.tar.gz)

Then I try to cmake the whole thing only to get this: 

jiewen@A-M14xR2:~$ ls
bin        examples.desktop       Music      Videos
Desktop    ffmpeg_build           Pictures   youtubevideo2.avi
Documents  ffmpeg_sources         Public     youtubevideo2.mp4
Downloads  Firefox_wallpaper.png  Templates
jiewen@A-M14xR2:~$ cd Downloads
jiewen@A-M14xR2:~/Downloads$ ls
document.pdf              skype-ubuntu-lucid_4.3.0.37-1_i386(1).deb
pidgin-lwqq-0.4.0         skype-ubuntu-lucid_4.3.0.37-1_i386.deb
pidgin-lwqq-0.4.0.tar.gz
jiewen@A-M14xR2:~/Downloads$ cd pidgin*
jiewen@A-M14xR2:~/Downloads/pidgin-lwqq-0.4.0$ ls
adium      cmake           debug.sh      README.md
AUTHORS    CMakeLists.txt  License       res
build      config.h.in     po            src
ChangeLog  CREDIT          README-en.md  ubuntu-online-account
jiewen@A-M14xR2:~/Downloads/pidgin-lwqq-0.4.0$ cd build
jiewen@A-M14xR2:~/Downloads/pidgin-lwqq-0.4.0/build$ cmake ..
-- checking for module 'purple'
--   package 'purple' not found
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:283 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:337 (_pkg_check_modules_internal)
  CMakeLists.txt:21 (pkg_check_modules)


-- checking for module 'lwqq>=0.4.0'
--   package 'lwqq>=0.4.0' not found
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:283 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:337 (_pkg_check_modules_internal)
  CMakeLists.txt:23 (pkg_check_modules)


libpurple version:Package purple was not found in the pkg-config search path.
Perhaps you should add the directory containing `purple.pc'
to the PKG_CONFIG_PATH environment variable
No package 'purple' found
libpurple version outdate
CMake Error at src/CMakeLists.txt:41 (install):
  install TARGETS given no LIBRARY DESTINATION for module target "webqq".


===============pidgin-lwqq flags===============
-- Native Language Support : true
-- Install Path            : 
===============================================
-- Configuring incomplete, errors occurred!
See also "/home/jiewen/Downloads/pidgin-lwqq-0.4.0/build/CMakeFiles/CMakeOutput.log".
jiewen@A-M14xR2:~/Downloads/pidgin-lwqq-0.4.0/build$ 

I'm so confused can someone help me? Thank you.

---

