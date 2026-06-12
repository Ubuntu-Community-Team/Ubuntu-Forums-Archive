---
title: "compiling smb4k from source"
date: 2016-08-20
forum: General Help
---

### Post by philipwmirabelli on 2016-08-20
Hello, I am having trouble installing the updated version of SMB4K (version 1.9..65) which is not available on synaptic. I am running kubuntu 16.01 1 LTS with plasma 5.5.5. I have managed to unzip the tar file and have navigated to the correct folder using "cd" on terminal, when I follow the instructions on the "readme" file from the program I get error messages in terminal.  This is pasted below, if anyone has any idea why I get these error messages I'd appreciate some feedback thanks! Philip

[COLOR=#800080]"root@philip-LIFEBOOK-P702:/home/philip/Downloads/smb4k-1.9.65# cmake -DCMAKE_INSTALL_PREFFIX=$(kde4-config --prefix) \-DCMAKE_BUILD_TYPE=Release1.9.65
-- The C compiler identification is GNU 5.4.0
-- The CXX compiler identification is GNU 5.4.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
CMake Error at CMakeLists.txt:12 (find_package):
  Could not find a package configuration file provided by "ECM" (requested
  version 1.1.0) with any of the following names:

    ECMConfig.cmake
    ecm-config.cmake

  Add the installation prefix of "ECM" to CMAKE_PREFIX_PATH or set "ECM_DIR"
  to a directory containing one of the above files.  If "ECM" provides a
  separate development package or SDK, be sure it has been installed.


-- Configuring incomplete, errors occurred!
See also "/home/philip/Downloads/smb4k-1.9.65/CMakeFiles/CMakeOutput.log"."
[/COLOR]

---

### Post by steeldriver on 2016-08-20
You will need to install the [extra-cmake-modules](http://packages.ubuntu.com/xenial/extra-cmake-modules) package I think

---

### Post by philipwmirabelli on 2016-08-20
ok thanks I have done that, and it works ok, many thanks!

---

