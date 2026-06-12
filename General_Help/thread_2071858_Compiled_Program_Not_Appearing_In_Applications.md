---
title: "Compiled Program Not Appearing In Applications"
date: 2012-10-16
forum: General Help
---

### Post by STOMPY05 on 2012-10-16
Hi all I am new to this forum and not sure if this is in the correct section.

I have just compiled my first program from source (Desmume-0.9.8).

I used check install to create a .deb package from which I installed the program.

Everything went fine but I was wondering how I get it to install the program short cut's in the "Applications" section.

Any help would be appreciated.

I am using Ubuntu 12.04!

---

### Post by Cheesemill on 2012-10-16
You need to create a .desktop file for it.

Take a look at the contents of the .desktop files in /usr/share/applications to get an idea of the syntax.

---

### Post by STOMPY05 on 2012-10-16
Thanks for the help :)

Can this be added to the .deb file so I don't have to do this for every compiled program?

---

### Post by erinender987 on 2012-10-16
Go to terminal type "ls"you can see then some directory then type "cd Desktop " to put the file on desktop you have to remember the first latter will be capital latter for any directory .then type "gedit new.c" hare new is file name and ".c" is the extension. then you can see a editor type your c code  and save it . close the editor again go back your terminal type "gcc new .c  -o new"  then you can see a object file on your desktop if your compilation is completed without error to see your program  go back terminal and type "./new"

lets try, If any problem please inform me ...):P



[cheap printer ink](http://www.peachtreeink.com)

---

### Post by Cheesemill on 2012-10-16
> **STOMPY05 said:**
> Thanks for the help :)

Can this be added to the .deb file so I don't have to do this for every compiled program?
That's up to the developer.

Usually you get the .desktop file bundled in as part of the source code. A lot of the apps that I have compiled in the past have automatically added themselves to the applications menu.

---

### Post by STOMPY05 on 2012-10-16
Thanks guys.

I noticed it actually did create a .desktop file in /usr/local/share/applications.

This didn't appear in the application tab until I logged out.

Anyway the help is appreciated.

---

