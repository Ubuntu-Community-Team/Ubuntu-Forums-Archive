---
title: "error compile gostcrypt"
date: 2016-01-26
forum: General Help
---

### Post by thinkalone2 on 2016-01-26
#sorry for my bad english 
Hi
i want install gostcrypt this command  [http://linuxg.net/how-to-install-gostcrypt-1-0-on-ubuntu-14-04-and-derivatives/](http://linuxg.net/how-to-install-gostcrypt-1-0-on-ubuntu-14-04-and-derivatives/) on the lts 14.04  i do step to step
but when run "make" show error 
how to fix?


```
 
Compiling Application.cpp
In file included from /usr/include/wx-3.0/wx/stdpaths.h:185:0:
/usr/include/wx-3.0/wx/unix/stdpaths.h: In static member function ‘static GostCrypt::FilePath GostCrypt::Application::GetConfigFilePath(const wxString&, bool)’:
/usr/include/wx-3.0/wx/unix/stdpaths.h:56:5: error: ‘wxStandardPaths::wxStandardPaths()’ is protected
     wxStandardPaths() { }
     ^
TextUserInterface.h:101:19: error: within this context
In file included from /usr/include/wx-3.0/wx/stdpaths.h:185:0:
/usr/include/wx-3.0/wx/unix/stdpaths.h: In static member function ‘static GostCrypt::DirectoryPath GostCrypt::Application::GetExecutableDirectory()’:
/usr/include/wx-3.0/wx/unix/stdpaths.h:56:5: error: ‘wxStandardPaths::wxStandardPaths()’ is protected
     wxStandardPaths() { }
     ^
TextUserInterface.h:126:47: error: within this context
In file included from /usr/include/wx-3.0/wx/stdpaths.h:185:0:
/usr/include/wx-3.0/wx/unix/stdpaths.h: In static member function ‘static GostCrypt::FilePath GostCrypt::Application::GetExecutablePath()’:
/usr/include/wx-3.0/wx/unix/stdpaths.h:56:5: error: ‘wxStandardPaths::wxStandardPaths()’ is protected
     wxStandardPaths() { }
     ^
TextUserInterface.h:131:35: error: within this context
make[1]: *** [Application.o] Error 1
make: *** [all] Error 2



```

---

### Post by spjackson on 2016-01-26
In the URL you mention and also here [https://www.gostcrypt.org/wiki/doku.php?id=compilation_installation:compilation:linux:ubuntu](https://www.gostcrypt.org/wiki/doku.php?id=compilation_installation:compilation:linux:ubuntu) wxWidgets 2.8 is used. You are using wxWidgets 3.0 and it looks like that is not compatible. I suggest you try building with 2.8 instead.

---

### Post by thinkalone2 on 2016-01-26
> **spjackson said:**
> In the URL you mention and also here [https://www.gostcrypt.org/wiki/doku.php?id=compilation_installation:compilation:linux:ubuntu](https://www.gostcrypt.org/wiki/doku.php?id=compilation_installation:compilation:linux:ubuntu) wxWidgets 2.8 is used. You are using wxWidgets 3.0 and it looks like that is not compatible. I suggest you try building with 2.8 instead.how to downgrade or install wxWidgets 2.8 ?

---

### Post by steeldriver on 2016-01-26
There should be no conflict between libwxgtk2.8-dev and libwxgtk3.0-dev (i.e. both packages can be installed on the system)

Just go ahead and install libwxgtk2.8-dev as indicated in the "Install the needed dependencies" section of the page you linked

---

