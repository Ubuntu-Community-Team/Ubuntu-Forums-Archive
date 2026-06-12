---
title: "Laptop ACPI functions"
date: 2005-04-16
forum: General Help
---

### Post by Mr Wonka on 2005-04-16
Hello all.

This is my first post so please bear with me. 

Firstly, Ubuntu is by far the most human friendly distro that I've had the pleasure to use. In 99% of my case 'IT JUST WORKS' [SIZE=1](TM)[/SIZE]. After fiddling to death with fedora core 1 this is such a breeze. Nice one. A big thanks to the developers.

The problem is this. I'm setting up my laptop to use all the acpi functions. I've got suspend to hard disc and suspend to Ram working and am now trying out the LID functions. If I close my lid and then open it the screen has blanked (I'm assuming that thats correct) but it does not come back again. I have to hit Alt-f7 and then X pops back up as normal. 

After having a look at the 'lid.sh' script in the /etc/acpi directory and completly pulling it apart I can tell you why this happens. The script uses 'fgconsole' to obtain the current console and then switches the console to 12. It never gets to switch console back as it coded to do (by pulling the original console value from a variable) as the command 'fgconsole' fails.

Running 'fgconsole' in a console returns 'Couldnt get a file descriptor referring to the console'. Not the nessesary number. Running 'sudo fgconsole' returns '7' i.e. it works.

How can I get this script to utilise fgconsole correctly? It's a pain having to hit buttons to see anything.


Thanks for any help
Mr Wonka

---

