---
title: "Problem with gtkmm"
date: 2014-03-23
forum: General Help
---

### Post by frank37 on 2014-03-23
I'm fairly new to programming in C++ and very new to Linux. I have been compiling and running programs just fine for a while now. Then, I go to use gtkmm, and this error comes up on the compiler:

window.cpp:1:19: fatal error: gtkmm.h: No such file or directory
 #include <gtkmm.h>
                              ^
compilation terminated.

This results after trying to compile this code, just to see if gtkmm would work:

#include <gtkmm.h>
int main()
{
return 0;
}

I've checked and I have both folders for gtkmm-2.4 and gtkmm-3.0 in /usr/include. Thank you for the help.

---

