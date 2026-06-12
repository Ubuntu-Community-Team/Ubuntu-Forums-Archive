---
title: "ftp in etc/apt/sources.list"
date: 2006-11-06
forum: General Help
---

### Post by newbie_jhay on 2006-11-06
hi guys, just want to ask if there is any way i could bypass the firewall whenever i am installing via apt-get from an ftp site.

here's the case, i need to install a specific software in my workstation at the office, and the instruction on their website indicates that i need to edit my /etc/apt/sources.list file and add the ftp site to it. so i followed all the instructions they have provided but the problem is whenever i am running "apt-get update" it usually fails to update from the ftp site. i've also tried to download the files thru an ftp session and the "wget" command but to no avail.

so what i did is that i tried doing the same thing at home and i was successful in downloading the files via "wget". i tried to do some research on the case and i came to the conclusion that our company's firewall might be the one that prevents me from downloading the said files.

now, my questions is: could i set the ftp site in the sources.list to be passive? its just a suggestion from a friend, though we're both not sure if that's even possible... by the way, the best possible option for me is to make it work via apt-get since the software i need to install would need tons more of additional software from the repositories, so i really, really need your help....

i'll be waiting for your replies... thanks in advance!:D

---

