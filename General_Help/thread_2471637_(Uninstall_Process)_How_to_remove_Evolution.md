---
title: "(Uninstall Process) How to remove Evolution?"
date: 2022-02-05
forum: General Help
---

### Post by csae2608 on 2022-02-05
Hello ,


today i thought to check the Processes running in Background to see how the Linux Desktop performs
(actually i wanted to check the Graphics Card Performance) on Linux Ubuntu 18.04 LTS

and in doing so found some processes running in background that i don§t seem to use actively,

what caught my attention is the Process "Evolution" which i remember from Previous Debian releases as a Mailprogram and since i use Thunderbird think could make less use of it/would like to disable/uninstall the process.


However, when i try to 

"sudo apt autoremove evolution" a lot of pgrams get selected which id ont want to include in the uninstall process.


Please help to remove the pgram in the proper way, thanks!


[URL="https://ibb.co/4Wf7HNP"]https://ibb.co/4Wf7HNP

[https://ibb.co/n1hcSTL](https://ibb.co/n1hcSTL)
[/URL]

---

### Post by mIk3_08 on 2022-02-05
> **csae2608 said:**
> Hello ,


today i thought to check the Processes running in Background to see how the Linux Desktop performs
(actually i wanted to check the Graphics Card Performance) on Linux Ubuntu 18.04 LTS
and in doing so found some processes running in background that i don§t seem to use actively,
what caught my attention is the Process "Evolution" which i remember from Previous Debian releases as a Mailprogram and since i use Thunderbird think could make less use of it/would like to disable/uninstall the process.
However, when i try to 
"sudo apt autoremove evolution" a lot of pgrams get selected which id ont want to include in the uninstall process.
Please help to remove the pgram in the proper way, thanks!


[URL="https://ibb.co/4Wf7HNP"]https://ibb.co/4Wf7HNP

[/URL][https://ibb.co/n1hcSTL](https://ibb.co/n1hcSTL)


I think removing this evolution you say is removing the Thunderbird.   You know what Thunderbird is one of the best programs here in Ubuntu  Linux Operating System. I usually use this program for chat and my  email. well, if you want to remove this Thunderbird I think you can  easily do this commands ```
sudo apt-get remove programname" and "sudo  apt-get --purge remove programname
``` Good Luck and Cheers

---

### Post by Impavidus on 2022-02-05
You can remove evolution. Don't use autoremove on it, just remove. Then look at the list of autoremovable packages. If you want to keep them, mark them as manually installed. That's easy in synaptic, but apt can do it to. If you tell apt to install a package that's already installed, it will be marked as manual. If you don't know what a packige is for, its probably safe to autoremove.

Also run autoremove once before attempting to remove evolution. You may already have some autoremovable packages.

---

### Post by deadflowr on 2022-02-05
Evolution has a sub package, if you can call it that, called evolution-data-server.
That package is required for the Ubuntu desktop.
And it's what all those processes relate to.

It's not the full evolution email package you think it is and my recommendation is to ignore it.

---

### Post by csae2608 on 2022-02-07
thanks for your help,

i checked again, the only package that would be "selectable" in terminal is in fact "evolution-data-server" and those processes run in background, although i do nothing with "evolution", so i am wondering if mlk3_08 is right and it has something to do with Thunderbird?

would like to disable those processes, if possible.[https://ibb.co/zQbm59F](https://ibb.co/zQbm59F)

---

### Post by Holger_Gehrke on 2022-02-07
'evolution' is not just an email client, it's a complete personal information management (address book, calendar including to-do lists, notes and email). The back end for all these functions is evolution-data-server. The Gnome desktop uses this back end for example to store your online accounts. Without it Gnome would not work correctly, so either leave it alone or switch to another desktop.

Holger

---

### Post by csae2608 on 2022-02-07
aliright, good explanation, very helpful, thanksù!

---

