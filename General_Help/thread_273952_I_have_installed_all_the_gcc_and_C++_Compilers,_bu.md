---
title: "I have installed all the gcc and C++ Compilers, but cant find them in $PATH?!?"
date: 2006-10-09
forum: General Help
---

### Post by Podgepod on 2006-10-09
Hi I have recently (Yesterday) installed Dapper Drake. When trying to configure  the error message I get is "no accdeptable C compiler found in $PATH" 
I have done all the obviuse things to try and fix this (I Think). such as apt-get install build-essential; apt-get install gcc etc.
They seem to install correctly with no errors, but I still cant compile...
If I type gcc i get "command not found"
If I type locate *gcc* I get a list as long as my arm, showing me various locations of gcc.
I then try to export these locations to the $PATH and configure again...Adn I get the same error message about not finding acceptable C compiler.

Please Help

---

### Post by sedefcho on 2006-10-09
Hi, 
I have a similar problem. But why do you say after you do:
apt-get install build-essential
you get no errors?
What I get is an error message saying
something like "No build-essential package found".
I looked in the file which defines where Ubuntu
should search for packages but ... Well these
locations are all on the web and actually I am trying
to install build-essential in order to install
roaring penguin (a PPPoE client) in order to get
my internet running (my ISP offers PPPoE internet).
So I don't really know how to proceed. Maybe this 
build-essential is somewhere locally on my hard drive
but I do not know where. 
I am quite a newbie with Ubuntu as it becomes obvious
although I had RedHat for about 3 years.

Hope someone may help or point me to some other
resource on the web.

---

