---
title: "Simple problem"
date: 2012-12-23
forum: General Help
---

### Post by josuelopes on 2012-12-23
My question is refering to this [one]("http://ubuntuforums.org/showthread.php?t=1034762")

I have the same problem and its annoying please tell me what do i have  to input in the terminal (the exact words) to solve this thing? I dont  know if it matters but i tried to find the "options" file with command  ls and it doesn't find it...

btw i dont know how to exit the ctrl+atl+F1 "terminal".

---

### Post by Bashing-om on 2012-12-23
josuelopes; Hi !

Let's be clear about your question;
Do I understand you want to insert a boot parameter into the kernel boot line ?

And to exit a terminal just type "exit" (with out the quotes).

Terminal tutorials to help you on your way:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://beginlinux.com/twitter/1094-the-beginners-guide-to-the-ubuntu-terminal](http://beginlinux.com/twitter/1094-the-beginners-guide-to-the-ubuntu-terminal)
[http://ubuntuforums.org/showthread.php?t=1417116](http://ubuntuforums.org/showthread.php?t=1417116)
[http://freshtutorial.com/basic-ubuntu-command-tutorial-for-beginners/](http://freshtutorial.com/basic-ubuntu-command-tutorial-for-beginners/)

These I expect will keep you occupied for a bit, good starting points.
[INDENT]my effort to help <== BDQ

[/INDENT]

---

### Post by GameX2 on 2012-12-23
> **Bashing-om said:**
> And to exit a terminal just type "exit" (with out the quotes)

Josuelopes is referring to the virtual Terminal, reached by pressing CTRL-ALT-F1 to CTRL-ALT-F6;
To exit a virtual terminal and return to the Graphical User Interface, simply press CTRL-ALT-F7.

---

### Post by josuelopes on 2012-12-23
I understand that it should bem looking for a way to solve this, but the thing is that a i dont have the time to do it, please i have a project that needs to be concluded in a few day, all that is in that pc and i need help really. I knew it had something to do with kernel, but i dont have the expirience to use it (also i read somwhere that i have to install something). Please help

---

### Post by josuelopes on 2012-12-23
I'm a little desperade over here so... The loop that apears in the terminal is:
...
[14770.056800] ata1.00: status: { DRDY ERR }
[14770.058560] ata1.00: error: { UNC }
[14775.977705] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[14775.979463] ata1.00: irq_stat ox40000008
[14775.981223] ata1.00: failed command: READ FPDMA QUEDED
[14775.982960] ata1.00: cmd 60/08:00:b8:cb:56/00:00:2a:00:00/40 tag 0 ncq 4096 in
[14775.982961]          res 41/40:00:b8:cb:56/00:00:2a:00:00/40 Emask 0x409 (media error) <F>
[14775.986450] ata1.00: status: { DRDY ERR }
[14775.991845] ata1.00: error: { UNC }
...
and when it stops, this is what i get:
end_request: I/o error, dev sda, sector 710331320

i have no idea what it is and i really need a help, the kind of "ubuntu for dummies" please

---

### Post by fdrake on 2012-12-23
> **josuelopes said:**
> I understand that it should bem looking for a way to solve this, but the thing is that a i dont have the time to do it, please i have a project that needs to be concluded in a few day, all that is in that pc and i need help really. I knew it had something to do with kernel, but i dont have the expirience to use it (also i read somwhere that i have to install something). Please help

looking very quickly there are 2 possible resons: bad hdd or bug in the kernel?  Iif you need to get the data for your project quickly i suggest you to use a live usb/cd and mount the hdd trying to retrive at least the data that you need for the project , Back up what you need and use anothe pc for your business. You can then take your time into installing a fresh install or debugging the kernel

---

### Post by Bashing-om on 2012-12-23
+1 for fdrake's advise !

In addition, check your hard drive with ubuntu's disk utility.
version 12.04: dash->enter search term "disk utility"-> icon below the search box-> click on the icon to activate disk utility.

If That hard drive is failing and has valuable data on it; do not mess around, save the data!

[INDENT][INDENT][INDENT]my humble opinion <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by josuelopes on 2012-12-24
Thank you for both  your replies. It's actually a bug and i know that because i also have windown installed in another partition and it runs normally. So I what should i do? 
ps: i spend all night backing up my files, but thanks for the tip :)

---

### Post by josuelopes on 2012-12-24
come on people i really need help

---

### Post by steeldriver on 2012-12-24
I don't know exactly what you're trying to do - it would have been helpful if you'd explained it in your first post rather than expecting people to trawl through the 3 page thread in your link

*If* you are trying to add a modprobe conf entry as described in that thread, then you could do it with

```
echo "options libata noacpi=1" | sudo tee -a /etc/modprobe.d/libata.conf
```and then reboot. The name of the conf file is arbitrary but it will help you remember why you created it if you give it a name related to its purpose.

DISCLAIMER: I have no idea if that will actually solve your problem and take no responsibility if it breaks other stuff!

---

