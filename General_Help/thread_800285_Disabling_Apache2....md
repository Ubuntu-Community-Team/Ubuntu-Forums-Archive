---
title: "Disabling Apache2..."
date: 2008-05-19
forum: General Help
---

### Post by Bill42 on 2008-05-19
Guys,

I know this issue has been discussed, but using the suggestions in those threads were of no help..

Tried:  
1. "sudo update-rc.d -f apache2 remove" and although I got back a message that indicated the command was successful, on the next boot apache2 was back...
2. "sysv-rc-conf" and deleted all the run levels for apache2, although my changes continued to be reflected in the display (on subsequent calls) still on the next boot apache2 was back...

I am not an experienced Linux/Ubuntu user but it appears that there is some override going on in the boot process that insists on loading apache2. I do not want to un-install apache I just want to disable it until such a time as it is needed (which is seldom...)

Regards,

Bill42

---

### Post by cdtech on 2008-05-19
Check your runlevel: runlevel

Then cd into that directory - cd /etc/rc2.d

Check and make sure that the S91apache2 link is changed to K91apache2

The K's will not launch at startup the S's do, in the order of their numbering scheme.

---

### Post by Bill42 on 2008-05-19
Thanks for the quick reply..

I checked the "runlevel" and got back the following: N 2 (with a space between the two characters)

I looked in the suggested directory and all the other directories having a name with the form rcx.d and found no filename with word apache embedded in it at all...

Regards,

Bill42

---

### Post by Bill42 on 2008-05-20
Guys;

I am not having any success in disabling Apache2. Several of the things I have tried seem to work but after rebooting it is back again... It appears to have something to do with "upstart". My apologies for being a mostly clue-less in regard to Linux. What I am looking for is a way to ONLY start Apache2 manually. That seems a simple idea...can anyone help??

Regards,

Bill42

---

