---
title: "Having and issue with cmake"
date: 2017-01-29
forum: General Help
---

### Post by donniecash on 2017-01-29
Hello everyone, 

Every time i try to compile this directory in cmake, I get this error. 


> donald@donald-desktop:~/fastermelee$ sudo cmake ../Ishiiruka/
x86_64
ALSA found, enabling ALSA sound backend
ao NOT found, disabling ao sound backend
bluez NOT found, disabling bluetooth support
PulseAudio NOT found, disabling PulseAudio sound backend
OpenAL found, enabling OpenAL sound backend
X11 support enabled
Xrandr not found
-- Checking for module 'xi>=1.5.0'
--   
CMake Error at /usr/share/cmake-3.5/Modules/FindPkgConfig.cmake:367 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-3.5/Modules/FindPkgConfig.cmake:532 (_pkg_check_modules_internal)
  CMakeLists.txt:564 (pkg_check_modules)


-- Configuring incomplete, errors occurred!
See also "/home/donald/fastermelee/CMakeFiles/CMakeOutput.log".
See also "/home/donald/fastermelee/CMakeFiles/CMakeError.log".



Can someone tell me what the xi>=1.5.0 module is? can't find anything on it....

Thanks

---

### Post by Perfect Storm on 2017-01-29
you need libxi-dev

also it says you're missing Xrandr 


libxrandr-dev

so:
```
sudo apt-get install libxi-dev libxrandr-dev
```

---

