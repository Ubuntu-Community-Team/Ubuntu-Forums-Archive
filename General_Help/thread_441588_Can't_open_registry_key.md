---
title: "Can't open registry key?"
date: 2007-05-12
forum: General Help
---

### Post by JellyBean on 2007-05-12
Hi.

I was just about to install Ubuntu using Wubi, but I get the following error message appearing 3 times after I open the Wubi exe:

"Can't open registry key! (2)"

After I 'OK' the 3 error messages the GUI loads up.

Does anyone know what this means? Is it safe for me to go ahead and install anyway?

Any advice would be appreciated! Thanks.

---

### Post by Jerick on 2007-05-13
What version of Windows are you using to run it? I used Vista for my install and it [sorta] works right (see posts in [http://ubuntuforums.org/showthread.php?t=440877&page=2]("http://ubuntuforums.org/showthread.php?t=440877&page=2"))

---

### Post by JellyBean on 2007-05-13
I'm running it on Windows XP. It's strange because it looks like no one else has been having the same problem.
If you need any more information, just let me know.

---

### Post by JellyBean on 2007-05-13
Just went ahead and installed Ubuntu anyway. Everything seems to go fine until it freezes at 33% during the virtual disk format.
I tried re-installing it, but the same thing happens again.
Alt-F4 shows no activity both times.

Is there anything I can do?

---

### Post by robbielink on 2007-05-13
I'm having this same problem. XP sp2 on a Compaq laptop. It gives 3 "Ubuntu can't open registry key (2)"  error warnings. It then completes the installation (downloads Ubuntu) but when I restart I just get normal Windows startup so I think it must not be setting the registry key it needs to set for the Ubuntu boot option. I tried turning off firewall/anti-virus and reinstalling but that didn't help. I've searched the web but can't find any other mention of this issue.
Anyone know what registry changes Wubi needs to make to give the Ubuntu boot option?

---

### Post by ago on 2007-05-13
Only registry change is to store the installation path and a few other settings used by the uninstaller. Wubi also tries to read those settings at the beginning to see if a system is already installed, but even if the settings are not there it should not raise an error. None of the registry settings is really essential.

---

### Post by ecology2007 on 2007-05-14
I am pretty sure this message box pops up because wubi can not find any network card.
Are you sure you have a least one ?
Anyway this will be fixed in next revision.

---

### Post by ago on 2007-05-14
> **ecology2007 said:**
> I am pretty sure this message box pops up because wubi can not find any network card.
Are you sure you have a least one ?
Anyway this will be fixed in next revision.

I forgot about that. 

P.S. I tried wubi on a borrowed vista machine and had that (4 times), but did not have time to dig deeper and had no sources at hand to play with. There was a network card and a wireless card there. Never seen that on XP.

---

### Post by ecology2007 on 2007-05-14
That's because it is deep hidden in the registry_reader.nsh, some registry strings for network cards require this special reader.
The good point is that it has 7 different errors and gives us for the exact one. Once it has been solved we can disable all the error reports.
For this one it was :
"Can't open registry key! (2)"
I will have a look later.

About Vista, did you have time to try bcedit and maybe find its "remove entry" command ?

---

### Post by ago on 2007-05-14
> **ecology2007 said:**
> That's because it is deep hidden in the registry_reader.nsh, some registry strings for network cards require this special reader.
The good point is that it has 7 different errors and gives us for the exact one. Once it has been solved we can disable all the error reports.
For this one it was :
"Can't open registry key! (2)"
I will have a look later.

About Vista, did you have time to try bcedit and maybe find its "remove entry" command ?


No because the network connection was junk and could not download the ISO... That was my intention...

---

### Post by codecrazy on 2007-05-20
i got the same problem, but continued with the install. i have a toshiba satellite 1805-s204, and when i chose to boot into ubuntu (when it told me i neede to restart), it said something in the startup sequence about not being able to mount the disk. it continued with the install, but stopped midway by giving me an error. it then took me back to the setup menu.

---

