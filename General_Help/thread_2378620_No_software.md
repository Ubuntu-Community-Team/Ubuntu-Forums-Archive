---
title: "No software"
date: 2017-11-25
forum: General Help
---

### Post by drawstops2 on 2017-11-25
I have just installed Ubuntu 16 on a new PC and when I click on the software icon the page appears for only two seconds and then disappears.
Any suggestions please?
Many thanks
Richard.

---

### Post by Autodave on 2017-11-25
Did you make sure that all the updates are installed?  In a terminal type:

sudo apt-get update

You will then be asked for your password. Enter it: you will NOT see it being entered on the screen however.

After that has finished, type and run:

sudo apt-get update

When that is done, try your software center then. (You may have to reboot.)

---

### Post by drawstops2 on 2017-11-26
Thanks for reply.
Regret I am elderly and although I have used Ubuntu for many years I have never used the terminal as every time I have tried I am told it does not recognise the input;
Ubuntu installed all the updates when installing the o/s.

---

### Post by mörgæs on 2017-11-26
> **drawstops2 said:**
> ...I am told it does not recognise the input

Please post the exact output from the terminal (copy-paste).

---

### Post by RobGoss on 2017-11-26
Just copy and paste the commands like **Autodave** suggested it and it should run with no problems

---

### Post by Perfect Storm on 2017-11-26
> **Autodave said:**
> Did you make sure that all the updates are installed?  In a terminal type:

sudo apt-get update

You will then be asked for your password. Enter it: you will NOT see it being entered on the screen however.

After that has finished, type and run:

sudo apt-get **update**

When that is done, try your software center then. (You may have to reboot.)

Shouldn't it be sudo apt upgrade?

---

### Post by RobGoss on 2017-11-26
> Shouldn't it be sudo apt upgrade?

You are correct it should be **sudo apt upgrade** thanks for the sharp eye

---

### Post by drawstops2 on 2017-12-06
Sorry for the delay in thanking you all but have had a hospital visit.
Have done a re-install and now all is OK.
Am going to update to Ubuntu 17 in the next few days.
Marvellous forum - thank you all so much.
Richard,

---

