---
title: "Radeon 9600 ATI graphic Card - First time User and ubuntu Friend"
date: 2007-07-26
forum: General Help
---

### Post by solutionsforall on 2007-07-26
I hope this thread to be: "THE" place to solve this problem.

[COLOR="Blue"]
Scenario[/COLOR]:


-Dell Inspiron 8600 1.6 gighertz Notebook

-512 megabyte of memory

-60 gigabyte hard drive

-LCD Notebook

-[COLOR="Teal"]Radeon 9600 (ATI m10 rv 3[/COLOR]50)

-Wireless Pentium centrino mobile technology

-System>Administration> Restricted Drivers: ATI Accelerated Graphics Driver "Not enabled"

-Fresh Ubuntu 7.04 install

-System> preferences> Screen Resolution> 1024X768



[COLOR="Blue"]
Problem:[/COLOR]

-Screen "scrambles" any resolution over 1024X768 (breaks apart)
-Previous windows user able to get higher resolution


Sources:
- that have not worked previously (system crashed before b/c of faulty docs, advice, and websites)

[https://help.ubuntu.com/community/Fi...esolutionHowto](https://help.ubuntu.com/community/Fi...esolutionHowto) (some invalid commands)
IRC.freenode.net #ubuntu (advice lead to crash; changing xorg.config incorrectly)
Websites: Inaccurate advice.

[COLOR="Blue"]What I want:[/COLOR]

Better resolution given I had it with windows and all my drivers working effectively.



I Would love to use ubuntu linux effectively with all my drivers on this computer as did in windows.

I would appreciate a better transition into ubuntu-This is the first time my computer crashed, ever.

Expert advice on a simple issue such as resolution, I would appreciate.

Thanks,:)

-Solutionsforall

---

### Post by strabes on 2007-07-26
Follow [these](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b) instructions exactly.

---

### Post by solutionsforall on 2007-07-26
Is it these? And will this allow me [COLOR="Green"]resolution above the 1024X768?[/COLOR]

> 

Install from Ubuntu repositories (easier)
Instructions for 7.04 (Feisty)

* Install linux-restricted-modules and restricted-manager provied in the restricted repositories:

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

Open the restricted drivers manager included in 7.04 "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". This will hopefully enable fglrx in a painless way. If not, follow the instructions for Edgy.



I appreciate your help Sabes

-solutionsforall

---

### Post by solutionsforall on 2007-07-26
Sades/others who know about this-

After That direction I have now:

System>preferences>Screen Resolution

-1024X768
-800X600
-640X480

@ 60 Hertz


These are the only options:

I want to get above 1024X768 Screen Resolution.  Why can't I?  I was able to in windowsxp?


Do you see where I'm thinking?

-Solutionsforall:)

---

### Post by solutionsforall on 2007-07-26
I could also copy/paste my outputs for any inputs to better clarify the situation in the terminal. I also would like to know how to tell if my drivers are working and installed correctly. There are no "yellow" flags for those drivers that did not install properly as in windows, so I would imagine ubuntu has a better system for this to detect non-working drivers. However, I have not been able to detect them in system>preferences>hardware information.

-Solutionsforall

---

