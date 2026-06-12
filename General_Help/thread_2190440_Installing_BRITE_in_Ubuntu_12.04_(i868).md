---
title: "Installing BRITE in Ubuntu 12.04 (i868)"
date: 2013-11-27
forum: General Help
---

### Post by mulyead on 2013-11-27
Getting following error while installing BRITE (network topology genarator software in Ubuntu 12.04

akshay@ubuntu1204s:~/Downloads/BRITE$ make c++
make[1]: Entering directory `/home/akshay/Downloads/BRITE/C++'
g++ -Wall -c BriteMain.cc -g
In file included from /usr/include/c++/4.6/backward/strstream:52:0,
                 from Util.h:29,
                 from Parser.h:28,
                 from Brite.h:28,
                 from BriteMain.cc:28:
/usr/include/c++/4.6/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated. [-Wcpp]
In file included from Brite.h:29:0,
                 from BriteMain.cc:28:
Models/Model.h:31:18: fatal error: algo.h: No such file or directory
compilation terminated.
make[1]: *** [BriteMain.o] Error 1
make[1]: Leaving directory `/home/akshay/Downloads/BRITE/C++'
make: *** [c++] Error 2
akshay@ubuntu1204s:~/Downloads/BRITE$ startGUI
startGUI: command not found
akshay@ubuntu1204s:~/Downloads/BRITE$ cd ...
bash: cd: ...: No such file or directory
akshay@ubuntu1204s:~/Downloads/BRITE$ cd ..
akshay@ubuntu1204s:~/Downloads$ java-version
java-version: command not found
akshay@ubuntu1204s:~/Downloads$ cd ..
akshay@ubuntu1204s:~$ java -version
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>

What might be the problem ???

The documentation and download is from site [http://www.cs.bu.edu/brite/](http://www.cs.bu.edu/brite/)

Thanks in advance.....

---

### Post by heir4c on 2013-11-27
You must install java on the system. Also you need javac. (yes with a c at the back)
I try something out [COLOR="#0000CD"](I'm not an expert or do not know a thing about it, but I always do a little bit crazy with my system to try to help other people)[/COLOR].
So, Like it say in your post, java you can find in the packages he mentioned:
* default-jre
* gcj-4.6-jre-headless
* openjdk-6-jre-headless
* gcj-4.5-jre-headless
* openjdk-7-jre-headless

And javac you find in the packages (That's what I get when I try to install it):
 * default-jdk
 * ecj
 * gcj-4.6-jdk
 * gcj-4.7-jdk
 * openjdk-7-jdk
 * openjdk-6-jdk

I installed the 2 defaults 
[COLOR="#FF0000"]FYI: !!!
(many many packages will be installed, so you must choose if you want to do that. I don't now if there is a alternatively way to install something for having java and javac on your system. Maybe other members here can help you with that)  [/COLOR]
command:
```
sudo apt-get install default-jre default-jdk
```

After that I could do the command: [COLOR="#008000"]make all[/COLOR] (I used this command because in the ReadMe file they say to use this. I downloaded the first file of the download link. Here a direct link (But I don't now you have it directly, because I have to give my email, name and other info to download it, so let me now if you can download it from here or not): [http://www.cs.bu.edu/brite/download29az78ffhg50kl9/new/BRITE.tar.gz](http://www.cs.bu.edu/brite/download29az78ffhg50kl9/new/BRITE.tar.gz) )

I have to install g++ too because without it give also errors.

After all the terminal/install-stuff. You can start it with the command:
```
./brite &
``` 

Or go to the BRITE folder in the Download directory and doubleclick on the file with the name: brite
Than it will start. (If it just open it with gedit than post that here, but in 12.04 it must be working normal. In 13.10 and 14.04 there are settings changes done)

I hope this is a little bit help to get you started.

---

