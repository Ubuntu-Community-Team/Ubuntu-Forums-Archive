---
title: "Ubuntu Ascii Logo Program"
date: 2006-11-08
forum: General Help
---

### Post by lemix on 2006-11-08
Hello all ubuntu users, i dont post often but i thought i might share this creation with the public. There is some nice ascii art on [www.chris.com/ascii](www.chris.com/ascii) one of which is an ubuntu symbol(its under linux). ANYWAY i wrote it in c++ so it would pop up in a terminal, this is great for servers.

i wanted to make a clean Ubuntu server and make it have some neat looking features other than that moo ascii program so i wrote this simple program in C++

here is a screenshot...
[www.guihacker.com/snapshot1.png](www.guihacker.com/snapshot1.png)

here is the link to the executable file...
[www.guihacker.com/Ulogo.out](www.guihacker.com/Ulogo.out)

Here is the code, that i compiled with g++, if you want it. 

> 
#include <iostream.h>

int main()
{
cout<<"               .-. \n";
cout<<"         .-'``(|||) \n";
cout<<"      ,`\\ \\    `-`.               88                         88 \n";
cout<<"     /   \\ '``-.   `              88                         88 \n";
cout<<"   .-.  ,       `___:    88   88  88,888,  88   88  ,88888, 88888  88   88 \n";
cout<<"  (:::) :        ___     88   88  88   88  88   88  88   88  88    88   88 \n";
cout<<"   `-`  `       ,   :    88   88  88   88  88   88  88   88  88    88   88 \n";
cout<<"     \\   / ,..-`   ,     88   88  88   88  88   88  88   88  88    88   88 \n";
cout<<"      `./ /    .-.`      '88888'  '88888'  '88888'  88   88  '8888 '88888' \n";
cout<<"         `-..-(   ) \n";
cout<<"               `-`\n\n";

return 0;
}


Credit LGB/dew from [www.chris.com](www.chris.com) for the ascii work. i just wrote the simple program.

Feel free to give me no credit for this work, call it your own, redistribute.

---

### Post by lemix on 2006-11-08
I now realize you cannot download the bin file so until someone posts an resolution(because i just dont know at the moment) your just going to have to compile the source with g++.

---

### Post by po0f on 2006-11-08
lemix,

You could have just used [linux_logo](http://www.deater.net/weave/vmwprod/linux_logo/).

---

### Post by lemix on 2006-11-09
i was thinkin about just using a tux ascii. Its on the site. It would be very easy.

---

### Post by edboq on 2006-11-15
hi

newbie in linux, i've installed and configured linux-logo via apt.

i wanted to insert linux_logo in my ubuntu.
but how?

do i have to edit /etc/motd ? :( 

tanks in advance

---

### Post by po0f on 2006-11-15
edboq,

In a startup script, you'll have to have linux_logo output to /etc/motd.  [This link](http://www.deater.net/weave/vmwprod/linux_logo/USAGE) should help with the linux_logo side of things.  Towards the end of the page, there is a tip on how to get it working with Debian, should apply to Ubuntu equally.

---

