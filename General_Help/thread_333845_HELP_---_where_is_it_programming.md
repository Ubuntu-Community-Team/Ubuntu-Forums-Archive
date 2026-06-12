---
title: "HELP --- where is it? programming"
date: 2007-01-08
forum: General Help
---

### Post by noMoreWindows on 2007-01-08
Hi all, im new to ubuntu linux in fact 3hrs new. kindly give me LINKS where to get visual C++ and java for linux. I tried to install microsoft Visual studio (vC++) but it give me this error:

"No application suitable for automatic installation is available for handling this kind of file."

Am I missing something here, or they are not just compatible?

also am trying to install yahoo msgr but it also give me this error:

"Dependency is not Satisfiable: libgdk-pixbuf2"

to tell you frankly i have no idea what it meant. Can someone give me a quick tutor or links of answers.

thanks

---

### Post by neoflight on 2007-01-08
> **noMoreWindows said:**
> Hi all, im new to ubuntu linux in fact 3hrs new. kindly give me LINKS where to get visual C++ and java for linux. I tried to install microsoft Visual studio (vC++) but it give me this error:

"No application suitable for automatic installation is available for handling this kind of file."

Am I missing something here, or they are not just compatible?

also am trying to install yahoo msgr but it also give me this error:

"Dependency is not Satisfiable: libgdk-pixbuf2"

to tell you frankly i have no idea what it meant. Can someone give me a quick tutor or links of answers.

thanks
visual C++ is for windolls. if you want c++ for linux then install gcc (GNU compiler)
you need to open up a terminal (Application> accessories>terminal) and issue this command...

```
sudo aptitude install gcc-4,1 
```

you need to enter the admin (your user login) password  and it will install latest gcc... to need an interface there are several IDE s available for linux....search for 
"C++ IDE" in google....

or use synaptic package manager to install applications... (System>administration>synaptic  package manager)...

there is a plethora of [_documentation_]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") available for ubuntu.
go to the forum main page and browse through "beginner' section and its immensely helpful...make sure that you post in the apropriate forums so that you can get very good support...than this one ;) 

good luck and welcome

---

### Post by quartzy on 2007-01-08
> **noMoreWindows said:**
> Hi all, im new to ubuntu linux in fact 3hrs new. kindly give me LINKS where to get visual C++ and java for linux. I tried to install microsoft Visual studio (vC++) but it give me this error:

"No application suitable for automatic installation is available for handling this kind of file."

Am I missing something here, or they are not just compatible?

also am trying to install yahoo msgr but it also give me this error:

"Dependency is not Satisfiable: libgdk-pixbuf2"

to tell you frankly i have no idea what it meant. Can someone give me a quick tutor or links of answers.

thanks

If you are wishing to program, might I advice this:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29)

---

