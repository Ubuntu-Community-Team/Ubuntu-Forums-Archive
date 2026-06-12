---
title: "Synaptic package error"
date: 2005-10-16
forum: General Help
---

### Post by dhenjhidz on 2005-10-16
greetings,

im kinda new to linux but im giving it a try and so far i think it is really a better alternative to expensive operating system..but for some reason i am having a problem using the application synaptic package manager..i tried to install the package i found from the internet which is conexant_192-1ubuntu-1_i386.deb using "sudo dpkg -i conexant_192-1ubuntu-1_i386.deb" command, the installation wasnt completed because it cant find the internal modem device. after the failure of that installation i cant seem to use the Synaptic Package Manager and the apt-get command, i keep getting the error "E: The package conexant needs to be reinstalled, but I can't find an archive for it.". i tried to use the command "sudo apt-get remove conexant" but i still recieve the same error..

is there a way to fix this error?

is there a way to use the internal D-link hsf dial-up modem in ubuntu 5.04?

---

### Post by Emerzen on 2005-10-16
I'm not sure about installing the modem itself, but you can use Synaptic to remove the broken package.  Open up Synaptic->Settings->Filters.  Highlight Broken and click okay.  It should bring up any broken packages, which you should be able to completely remove w/ a right click on the package in Synaptic.

---

### Post by Emerzen on 2005-10-16
PS  I would searc the WIKI about installing a Conexant modem.

---

### Post by dhenjhidz on 2005-10-16
[QUOTE=Emerzen]I'm not sure about installing the modem itself, but you can use Synaptic to remove the broken package.  Open up Synaptic->Settings->Filters.  Highlight Broken and click okay.  It should bring up any broken packages, which you should be able to completely remove w/ a right click on the package in Synaptic.[/QUOTE]

hi emerzen,

thanks for replying to my post..i had tried doing what you had suggested..i opened synaptic package manager, input the password then i recieved the error again but i click ok then i went to settings > filters then i highlighted the broken and even checked  all of the checkbox for current, other and marked on the right side of the window but still nothing is displayed in the listbox of synaptic package column..it has always been like this since i tried to install the conexant package..it seems that synaptic cant find any package anymore and because of this, i cant install anything anymore..like when i try to search for wine, it cant find anything..not even those package that is already installed..i dont know..maybe this is like an internal error...

---

### Post by Emerzen on 2005-10-18
Sorry to take so long at gettting back to you.  When you open Synaptic, at the bottom left, almost greyed out, are dome stat's.  It should say something like x# of packages found, y#installed, z#broken, etc...  Is there a # listed for broken?

---

### Post by Emerzen on 2005-10-18
I forgot to mention...after setting up the broken filter as above, in Synaptic, you have to left-click on 'broken' in the pane on the left.  Sorry, I'm away from my home desktop and am trying to do this from memory.

---

### Post by dhenjhidz on 2005-10-26
[QUOTE=Emerzen]I forgot to mention...after setting up the broken filter as above, in Synaptic, you have to left-click on 'broken' in the pane on the left.  Sorry, I'm away from my home desktop and am trying to do this from memory.[/QUOTE]

synaptic still displays no package installed, broken or not installed.. like its not functioning anymore..i tried to install a package using dpkg and i receive the same error even if i use this program (The package conexant needs to be reinstalled, but I can't find an archive for it)..i tried to do a little reading about using the dpkg program and i found out that by using the command "sudo dpkg -r --force-remove-reinstreq conexant" i can force remove broken package but still with no success..here is the error dpkg gives:

user@Ubuntulinux:~$ sudo dpkg -r --force-remove-reinstreq conexant
Password:
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 71076 files and directories currently installed.)
Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 conexant
user@Ubuntulinux:~$ 

maybe if i can remove conexant from the list of packages of dpkg or synaptic  so that it will not look at this package i can make these programs work again..i cant install anything and i dont want to completely reinstall the whole operating system just because the package management program doesnt work anymore..but if need be..i guess i will have to

---

### Post by la leche jodia on 2005-12-09
In the first time, sorry for my english.

I'd got the same problem than you with the driver of my conexant modem, the solution was reinstall Ubuntu.

But now I've had the same problem again, but with the package facturlinex (is a contability program from la Junta de Extremadura).

The problem was the same: synaptic blocked, can't install anything because de package was broken, etc.

I thought the solution was search where dpkg "look", then I deleted the files and scripts "facturlinex" in /var/lib/dpkg/info, but that wasn't enough :( . Then I edited the file "status" in /var/lib/dpkg and I searched  for "facturlinex", when I founded the chain, I saw information about the package, I deleted all information and saved the file.

Inmediatly the upgrade icon became read  ;) and, now, I can run synaptic an update my system and all works fine.

I hope this information will be nice to you.

Regards

---

### Post by lignito on 2006-02-13
fantastic!!!it did work.Thanks!! I didn't had to reinstall the all thing or reformat!!

---

