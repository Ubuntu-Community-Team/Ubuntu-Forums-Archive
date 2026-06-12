---
title: "how to install CDT plugin for Eclipse Kepler"
date: 2013-08-30
forum: General Help
---

### Post by NGSG on 2013-08-30
Hi,
apologise for this rather naive and certainly stupid question, but I am a little bit confused.
I recently started to use Eclipse Kepler 4.3 on my Ubuntu and worked first with developping Java applications.
I want now to have C++ support as well. Of course, i could download the standalone application for C++ but for convenience, i would like to have it as plugin.
to do this, i did the following steps:
1) i selected in the menu: Help -> Install new software 

2) I followed the instructions given at this link [http://eclipse.org/cdt/downloads.php](http://eclipse.org/cdt/downloads.php) to install CDT:  I checked all packages because i was not sure.
    In the Add: I put Name: CDT and URL: [http://download.eclipse.org/tools/cdt/releases/kepler](http://download.eclipse.org/tools/cdt/releases/kepler)
3) I added the Linux Tools as described here: [http://wiki.eclipse.org/Linux_Tools_Project/PluginInstallHelp](http://wiki.eclipse.org/Linux_Tools_Project/PluginInstallHelp)
    namely: Help -> Install new software -> Add and put as:
    Name: Linux Tools
    URL: [http://download.eclipse.org/linuxtools/update](http://download.eclipse.org/linuxtools/update)
4) then i started again eclipse and created a new workspace for my c++ projects.
5) I created a new project from the Menu: File -> New -> C++ Project
    Project type: Executable -> Hello World C++ Project
    Toolchains: Linux GCC
 (I also tried Makefile project)
6) this produced the following HelloWorld.cpp file
```

#include <iostream>
using namespace std;
int main() {
	cout << "!!!Hello World!!!" << endl; // prints !!!Hello World!!!
	return 0;
}

```
Something is screwed up at here. Eclipse complains indeed already that it does not know about std or cout. I must have missed one important step here. I will be grateful if someone has some idea what could be wrong in the above steps.
No need to mention, that I fail to build it within Eclipse, since if i try to build the project, i get:
```

Errors occurred during the build.
Errors running builder 'CDT Builder' on project 'HelloWorld'.
Internal error building project HelloWorld configuration Debug
java.lang.NullPointerException
Internal error building project HelloWorld configuration Debug
java.lang.NullPointerException
Errors running builder 'CDT Builder' on project 'TestCPP'.
Internal error building project TestCPP configuration Debug
java.lang.NullPointerException
Internal error building project TestCPP configuration Debug
java.lang.NullPointerException
Errors running builder 'CDT Builder' on project 'toto'.
Internal error building project toto configuration Default
java.lang.NullPointerException
Internal error building project toto configuration Default
java.lang.NullPointerException

```

Thanks for your help here.

---

### Post by leg on 2013-08-31
It looks as though the project is trying to compile against a Java environment. Did you select a project template for C++ ? If not that simple check the build configs and see if you can switch it over to the C++ compiler.

---

### Post by NGSG on 2013-08-31
Hi,
I had a look at Stackoverflow, where I could find some hint about why the standard headers are not found:
[http://www.eclipse.org/forums/index.php/t/247954/](http://www.eclipse.org/forums/index.php/t/247954/)
I move my question there and will post the link here.
seems like i screwed things up by trying to use one single installation for both C++ and Java.
thanks again.

---

