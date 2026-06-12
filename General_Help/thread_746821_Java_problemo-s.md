---
title: "Java problemo-s"
date: 2008-04-05
forum: General Help
---

### Post by boardrfolife on 2008-04-05
Successfully installed ubuntu 7.10 on an old hp just to try out another OS. Basically you can't use the internet at my school until at least java is installed. I've googled and searched the forums on here for the past 8 hours and still no luck. Heres what I've tried.

1. Applications, add/remove - internet woun't connect to server downloads due to schools stupid firewall not having java installed yet. 

2. Booting firefox, install missing plugins comes up but when I click on it "no suitable plugins were found" how contradictory.

3. Package install of "sun-java5-plugin_1.5.0-15-0ubuntu1_i386.deb" Package installer opens, of course "Error: Dependency is not satisfiable: sun-java5-bin" Next I go online download all the dependencies and it all goes well until I actually get to sun-java5-bin. another dependency but this time its "sun-java5-jre. So I download that and circular dependencies. sun-java5-jre depends on sun-java5-bin. No way to install either.

4. Terminal, converted "sun-java5-plugin_1.5.0-15-0ubuntu1_i386.deb" to a bin. Ran the bin in terminal and it created "jrel.6.0_05" i then sudo ln-s the "libjavaplugin_oji.so" to both /firefox/plugins and /mozilla/plugins. I went into the folders and the files in it but its got a little circle with like a white x midway down on the left side of the icon. 

I then restarted firefox, typed "about:plugins" no java at all. Restarted computer and got the same information. Then I opened Terminal, typed this "java -version" heres the results:

java version "1.5.0"
gij (GNU jibgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions. There is NO warrenty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.



any help would be greatly appreciated.

---

### Post by keeler1 on 2008-04-06
I am not sure if you did this but if they are both dependencies of each other just have them install at the same time.

Instead of a command to install one, then the same command with the other package just put both package names in with the one command.  If they are the only dependencies of each other then this should work.

---

