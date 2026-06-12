---
title: "-e ** passwords don't match, try again"
date: 2008-04-08
forum: General Help
---

### Post by Reg Editor on 2008-04-08
Hello,I've been using the guide:


HOWTO &#8211; Install BT Voyager modem drivers


[http://ubuntuforums.org/showthread.php?t=140010&highlight=bt+voyager+105](http://ubuntuforums.org/showthread.php?t=140010&highlight=bt+voyager+105)

and like philipoflondon at post number 33,I'm stuck at the configuration program stage.

When I enter my ISP password,I get:

Type in your password (given by your provider):
[: 905: ==: unexpected operator
Type in your password again (for verification): 
[: 905: ==: unexpected operator
-e ** passwords don't match, try again


Does anyone know the cause of the problem and how to solve it?

Thank you if you can help.

---

### Post by dcstar on 2008-04-09
> **Reg Editor said:**
> Hello,I've been using the guide:


HOWTO – Install BT Voyager modem drivers


[http://ubuntuforums.org/showthread.php?t=140010&highlight=bt+voyager+105](http://ubuntuforums.org/showthread.php?t=140010&highlight=bt+voyager+105)

and like philipoflondon at post number 33,I'm stuck at the configuration program stage.

**When I enter my ISP password**,I get:

Type in your password (given by your provider):
[: 905: ==: unexpected operator
Type in your password again (for verification): 
[: 905: ==: unexpected operator
-e ** passwords don't match, try again


Does anyone know the cause of the problem and how to solve it?

Thank you if you can help.

Do you enter **only** the password, or do you add other things because the other thread has them?

---

### Post by Reg Editor on 2008-04-09
Yes,only the password.I tried several times.

Ubuntu 7.10 Gutsy Gibbon

---

### Post by Reg Editor on 2008-04-09
with a refined google search,i found a solution to the problem.now of course i have run into yet another

the solution was found on another forum:

QUOTE 
After a lot of digging around i found the solution to the problem. I found it on ubuntu forums, enter this to set bash as the default shell: sudo ln -sf /bin/bash /bin/sh 
Then type eciadsl-config-text, works like a dream, connects first time aswell. I am a beginner wanting to move from windows to linux and i never would have figured that out. Thank you for the driver and my apologies for taking up space in the forums


new problem,in the guide this is shown:


QUOTE 
user name: You should have been given an e-mail user name when you signed up
password: [i]Whatever[i]
provider: British Telecom
DNS1: Accept default
DNS2: Accept default
VPI: 0
VCI: 38
modem type: BT Voyager 105
VID1/PID1/VID2/PID2: accept defaults
modem chipset: GS7470
synch file: /etc/eciadsl/gs7470_synch03.bin
PPP mode: Accept default
is DHCP used? no
is a static ip used? no



but after this stage: modem chipset: GS7470 was completed,this appeared:


USB ALT INTERFACE for SYNCH process currently set to 0
Type in the USB ALT INTERFACE for SYNCH (1-digit decimal (0-5) 


followed by



USB ALT INTERFACE for PPPOECI process currently set to 1
Type in the USB ALT INTERFACE for PPPOECI (1-digit decimal (0-5) 


[i've tried a few choices,including 3 in case it means synch03.bin,even with 3 selected at the end this was included:
.bin file : /etc/eciadsl/synch01.bin]

reponse: WARNING: no synch .bin file found in /etc/eciadsl or subdirectories
Please check your driver installation!


then it moved on to: Select your PPP mode 

and eventally ends up with:



Configuration will be created with these values :

+ User : xxxxxxxxxx
+ Password : (hidden)
+ Provider : UK..Pipex UK
DNS 1 : 158.43.240.4
DNS 2 : 158.43.240.3
+ VPI/VCI : 0/38
+ Modem : BT Voyager 105
GS chipset : GS7470
VID1/PID1 : 1690/0215
VID2/PID2 : 1690/0215
ALT SYNCH : 1
ALT PPPOECI : 1
+ .bin file : /etc/eciadsl/synch01.bin
+ PPP mode : VCM_RFC2364
+ use DHCP : no
+ use static IP : no

Press ENTER to create 


i havent been asked to select a .bin file as far as i can tell,of course i want to select /etc/eciadsl/gs7470_synch03.bin

---

