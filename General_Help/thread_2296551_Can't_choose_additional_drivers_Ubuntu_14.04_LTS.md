---
title: "Can't choose additional drivers Ubuntu 14.04 LTS"
date: 2015-09-26
forum: General Help
---

### Post by melle2 on 2015-09-26
Hello! I recently changed drivers out of curiosity, but upon realizing that the AMD proprietary drivers were causing screen problems, I tried to go back to x.org x. It isn't letting me, though. A new option popped up saying 'continue using manually installed drivers', and the other drivers are grayed out and unclickable. How do I go back to the x.org video driver? 

Here is a pic of the options. Thanks in advance!

[ATTACH=CONFIG]264670[/ATTACH]

---

### Post by QIII on 2015-09-26
Hello!

Please don't paste large images in your posts.  There are users with slow connections and monthly data limitations.  You may actually cost the latter group money.

Use the attachment functionality by clicking the paper clip icon in the toolbar above the text entry box.

With regard to your driver:  How did you install it?

---

### Post by melle2 on 2015-09-26
Thanks for sizing that down for me! And the drivers were always there since i first installed ubuntu (Fresh install was sept 5th) but when I changed from x.org to fglrx, It grayed out all the other options and now i cant switch it from 'continiue using manually installed driver'

---

### Post by QIII on 2015-09-26
How did you install the fglrx driver?

---

### Post by melle2 on 2015-09-26
its been there

---

### Post by ajgreeny on 2015-09-26
Did you tick the box at installation to install proprietary packages and updates as you installed?  If so, that is probably how you now have the fglrx driver installed on your system.

Try running ```
sudo apt-get remove fglrx*
``` then logout and in again and see if that does the trick.

---

### Post by melle2 on 2015-09-26
> **ajgreeny said:**
> Did you tick the box at installation to install proprietary packages and updates as you installed?  If so, that is probably how you now have the fglrx driver installed on your system.

Try running ```
sudo apt-get remove fglrx*
``` then logout and in again and see if that does the trick.

DING DING DING! Thank you sir, this worked! The 'continue using manually installed driver option is gone, and the x.org driver was already selected when I logged back in. Thank you so much for your help, both of you. 

[SIZE=1]now how do i  mark the thread as [solved]?[/SIZE]

---

### Post by ajgreeny on 2015-09-27
Brilliant!  I am very happy that it worked for you.

It would be interesting to work out why the fglrx driver was not working as it should when you asked for it to be added at installation of the OS, meaning that the system should have added the optimum version of the driver automatically.

What hardware graphic card do you have?  Show the output of ```
lspci | grep VGA
``` if you're not sure.

---

