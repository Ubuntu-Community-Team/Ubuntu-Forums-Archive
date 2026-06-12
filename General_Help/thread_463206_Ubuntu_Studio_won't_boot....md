---
title: "Ubuntu Studio won't boot..."
date: 2007-06-03
forum: General Help
---

### Post by SHAW344 on 2007-06-03
I'm looking for help other than a total restore for my Windows XP machine....  A couple of weeks ago, I downloaded UBUNTU using the Wubi...  It worked well and installed without incident....
A day or so ago, I upgraded to UBUNTU STUDIO using the download from UBUNTUSTUDIO...   Immediately after the download, the system function perfectly... no glitches...  I shut down the system overnight and when I restarted it I had an error message:

"Failed to start X server (Graphical Interface) likely not set up correctly.."    That was yesterday..

Today, Sunday, 6/3, when I attempted to boot UBUNTUSTUDIO, I get the opening screen with the colors and thats it.... 

    Any suggestions are welcome...  
At this moment I've searched the web for information on uninstalling UBUNTU and I've printed out several pages for using the XP Recovery module....    Have taken that route as yet....  Thought I'd see what some one else might offer ....

                                            Thanks, 

                                                  Joe

---

### Post by wcbardwell on 2007-06-04
So are you planning on completely removing ubuntu from your machine?

---

### Post by SHAW344 on 2007-06-04
Do I want to fully remove UBUNTU from my system?
 At the moment I know of no other alternative.
I was in hopes that someone would respond who could direct me to the needed information to repair what I have on my machine...
I called up the wiki.x.org...  and I'm totally lost with what I found there....  
So the plan of attack seems to be do the Windows correction and remove UBUNTU, then do another down load of UBUNTU using Wubi.
I've encountered another problem, I've been unable to get to the repair feature of Windows XP.....
I'd really like to have UBUNTU or one of the LINUX OS's on my machine, as a dual boot...

---

### Post by roadrocket13 on 2007-06-07
:BUMP: :?:

i'm having the same problem. the install process went as expected until the first boot.
a warning comes up alerting me to the fact that my X Server may not be configured properly and then eventually spits me out to an extremely buggy command line. 
any help is greatly appreciated. thanks in advance.

---

### Post by lowmax on 2007-09-27
Hello guys

Same problem over here, but without the buggy command line. "Failed to start X server". Please help.

Total noob so bear with me please

Tried to reinstall my nvidia drivers using envy but i keep getting the error message "Bad luck, the kernel headers for the target kernel version could not be found and you did not specify other valid kernel headers to use". 

I try to "apt-get install linux-headers-2.6.20-lowlatency" but I get the following:

The following packages have unmet dependencies:
nvidia-glx-new: Depends: nvidia-kernel-100.14.11 but it is not installable
ubuntustudio-audio: Depends: ardour

I tried to "apt-get -f install" but i get errors with ardour, dont know if it has anything to do with the x server problem.

Thanks for your time

---

