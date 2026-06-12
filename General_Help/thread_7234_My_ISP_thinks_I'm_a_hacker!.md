---
title: "My ISP thinks I'm a hacker?!?"
date: 2004-12-05
forum: General Help
---

### Post by benjou on 2004-12-05
Hello

I manage to setup my lucent AMR softmodem on my travelmate 507t by some way I do not clearly understand. (I used the slmodem trick described elsewhere...)

Now, neither pppd nor the standard ubuntu dialup program (the one under computer->networking) does recognize it but wvdial does  (?!...)

So I sat up wvdail.config with the phone number of my ISP, my login and my password.

Now when I do sudo wvdial, I can hear my modem dialing and doing all the strange sort of noises that modems usually do. Then I get a message in the terminal in french, german, italian and english saying that trying to hack a network can lead you to jail for 3 years. Then the isp hang off....

My login and password are correct so whatelse can I configure to calm my ISP down and get him to let me connect to the internet?

Thanks a lot for your ideas..

---

### Post by Hendry on 2004-12-05
[QUOTE=benjou]

My login and password are correct so whatelse can I configure to calm my ISP down and get him to let me connect to the internet? [/QUOTE]

Did you contact your ISP and inform them of the problems you have? Also did you check the ISP homepage for information? Maybe you have to change a setting specific for this ISP..

---

### Post by jdong on 2004-12-05
are you SURE you're dialing your ISP, not some CIA access point?  :mrgreen:  :mrgreen:  :mrgreen:

---

### Post by benjou on 2004-12-06
Finally I could make it work by changing all "stupid mode" bits to 1 :-k 

I still get a warning message but I can connect (probably this message is sent by default...)

I have no idea what that stupid mode means (I'm probably too stupid to run in clever mode ?!?)


Other question:
I could have the "gnome modem" taskbar to dialup using wvdial by changing the command "pon" by "sudo wvdial". Now what command should I use to disconnect? (poff does not work of course...)

Thanks for your ideas...

---

### Post by shimon on 2004-12-06
[QUOTE=jdong]are you SURE you're dialing your ISP, not some CIA access point?  :mrgreen:  :mrgreen:  :mrgreen:[/QUOTE]
 or The cia of that contrey

---

### Post by clasqm on 2004-12-06
[QUOTE=benjou]

I could have the "gnome modem" taskbar to dialup using wvdial by changing the command "pon" by "sudo wvdial". Now what command should I use to disconnect? (poff does not work of course...)
[/QUOTE]

gksudo pof.wvdial

works for me ...

---

### Post by clasqm on 2004-12-06
<clearing throat>

I meant poff.wvdial of course. Serves me right for posting from my Windows computer at work!

---

