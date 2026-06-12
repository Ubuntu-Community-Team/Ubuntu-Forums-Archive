---
title: "Chrubuntu on C7 Chromebook"
date: 2013-05-03
forum: General Help
---

### Post by Ashensins on 2013-05-03
[COLOR=#333333][FONT=Ubuntu Beta]First off, This is my second time installing a ubuntu partition on my c7 chromebook. I re installed it to see if I could bypass the issues this time. NOPE. One issue is an error message at startup, something like: invalid iomem size. you may experience problems. Another is I want to update as it prompts me when I log in, but last time I did I bumped into this screen: Configuring grub-pc. I can check dev/sda or dev/sda7 and I have no idea which to check if not both. Should I just leave the update alone? OR does it run more smoothly with the update? Also it's not detecting a webcam for some reason. ONE MORE THING. There are like 4 unmounted disk images sitting in my devices folder from since I first started ubuntu. OEM, Two Root-A's and one called 26 gb filesystem. What these used for and are they needed? 
Sincerely Ubuntu NoOb-


[/FONT][/COLOR]

---

### Post by oldrocker99 on 2013-05-04
OK:
1. I get the invalid iomem size message too; bear in mind it says "you MAY experience problems." I haven't seen major problems myself.

2. When it asks about GRUB, it's safe to install it to /dev/sda as well as /dev/sda7. 

3. BY ALL MEANS, update the installation.

4. The webcam works for me; try installing the program cheese, a webcam controller/picture taker.

5. The other disk images are the Chrome OS' home; I keep them there, just in case I want to boot into ChromeOS. Since I can get all the Google goodness just using the Chrome browser within ChrUbuntu, I just basically keep ChromeOS as a backup in case Chrubuntu goes south (as it did for me yesterday when I tried updating to 13.04, and hung on installing a library). I just reinstalled Chrubuntu and went on my merry way.


6. BTW, you can boot more quickly from the OS Verification screen by hitting ctrl-d.

Good luck! You asked good questions.

---

### Post by nikopol on 2013-05-08
One caveat. I transferred files to the chrome is partition to have them available to use. Disaster struck with the chrome os boot detected "issues" and forced me to factory reinstall. All Linux partitions were goners and impossible to recover. It's not like I could not into knoppix and recover add I normally do given the locked boot system.

---

