---
title: "brother printer"
date: 2013-05-31
forum: General Help
---

### Post by s7c on 2013-05-31
hello, i'm trying to install brother printer hh-2280dw which i had no problems to do that in ubuntu 12.10. now i've decided to switch to ubuntu 12.04 and for some reasons following the same steps it doesn't work. 
i will try to describe the steps i'm using ad hopefully somebody would see what am i doing wrong:
1-i'm downloading the drivers [ATTACH=CONFIG]243338[/ATTACH]as you can see i don't have an option for 32 or 64 bit and i don't know which from those 2 deb ext is good for me so i have downloaded and tried both, with the specification that the second option is installed but the ubuntu software for some reason after installtion it doesn't show as it was installed...
2-i'm going to printers folder and click add, i chosee my printer and click forward and after it supposed to say driver installed but unfortunatly i get this window [ATTACH=CONFIG]243339[/ATTACH] so in order to get further with the process i click on activate and after i get kicked in the ass by this [ATTACH=CONFIG]243340[/ATTACH] which is the point i'm totally lost and angry and i don't like that much ubuntu...
any help will be much appreciated.

---

### Post by gifford on 2013-05-31
Sorry about your frustration. From the first link you listed for the driver, download both the LPR driver and the cupswrapper driver. Underneath the driver section on Brother's site it has a link for install instructions.
Follow the install instructions on the Brother's site to install the LPR and cupswrapper. This will get you up and running.

---

### Post by s7c on 2013-06-01
i thought i did, above description is the proof...can you be more precise?

---

### Post by gifford on 2013-06-02
There are a few items to do before the install, example as from the Brother site is: sudo mkdir /usr/share/cups/model. And also mkdir/var/spool/lpd if it does not already exist.
The install procedure is done via the terminal command line. Here is the link for the page on the Brother site for you particular printer. [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html) 
You need to install both the lpd and the cups wrapper drivers. Take your time and make sure you are following the directions correctly.
You will also need to install the brscan driver as well for scanning. There are instructions at the site for this as well.
Are you using a network or USB connection?

---

### Post by s7c on 2013-06-05
> **gifford said:**
> There are a few items to do before the install, example as from the Brother site is: sudo mkdir /usr/share/cups/model. And also mkdir/var/spool/lpd if it does not already exist.
The install procedure is done via the terminal command line. Here is the link for the page on the Brother site for you particular printer. [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html) 
You need to install both the lpd and the cups wrapper drivers. Take your time and make sure you are following the directions correctly.
You will also need to install the brscan driver as well for scanning. There are instructions at the site for this as well.
Are you using a network or USB connection?

i use USB, anyway i can't install following the instructions from brother site. i got allot of errors...
again, i have installed in the way i described in my first message using 12.10. i don't get why now in 12.04 i cannot use the same method...

---

### Post by rewyllys on 2013-06-05
> **s7c said:**
> i use USB, anyway i can't install following the instructions from brother site. i got allot of errors...
again, i have installed in the way i described in my first message using 12.10. i don't get why now in 12.04 i cannot use the same method...
Why you can't use the same method as you used in 12.04 is a question I can't answer, but I can suggest that you try using the driver-installer script that Brother provides at this [URL]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104")

I've had success using this script in several installations, and I hope you will find it similarly satisfactory.

---

### Post by s7c on 2013-06-07
> **rewyllys said:**
> Why you can't use the same method as you used in 12.04 is a question I can't answer, but I can suggest that you try using the driver-installer script that Brother provides at this [URL]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104")

I've had success using this script in several installations, and I hope you will find it similarly satisfactory.

thank you for taking your time to help me. it didn't worked that way though or it couldn't find the file or it said gunzip command is invalid. anyway, i unziped the document and made it executable and if i run it as an application didn't worked but i decided to run it in terminal so it was the right path to choose. finnaly i solved this annoying problem...

---

### Post by rewyllys on 2013-06-07
> **s7c said:**
> . . . . finnaly i solved this annoying problem...
Congratulations!  Glad to hear that you solved your problem.:D

---

