---
title: "installing idv"
date: 2007-01-19
forum: General Help
---

### Post by col_b on 2007-01-19
Hello,

I'm trying to install idv (integrated data viewer).  The file that I download is a .sh file, idv_2_0_linux-i386_installer.sh.

The instructions tell me to do the following:

On Unix, run the installer with sh (installer file name), (e.g., sh idv_2_0_linux-i386_installer.sh) in the directory where you saved this file. Follow the instructions in the installer's pop-up window. Once the IDV is installed, go to the directory you selected and type ./runIDV to start the IDV.

But when I type sh idv_2_0_linux-i386_installer.sh, I get the following:

cjbeaney@flux:~/Desktop$ sh idv_2_0_linux-i386_installer.sh
sh: Can't open idv_2_0_linux-i386_installer.sh

I also tried: 

sudo sh idv_2_0_linux-i386_installer.sh

But it also said that it couldn't open it.

Would anyone happen to know how I can install this .sh file?

Thanks in advance,
Col

---

### Post by DerHesse on 2007-01-19
ist that the actual location of the script?
try:

actual_scriptlocation $ sudo sh **./**idv_2_0_linux-i386_installer.sh

---

### Post by col_b on 2007-01-19
Thanks for the reply DerHesse.

I tried your suggestion, but was given the following:

cjbeaney@flux:~/Desktop$ sudo sh ./idv_2_0_linux-i386_installer.sh
sh: Can't open ./idv_2_0_linux-i386_installer.sh
cjbeaney@flux:~/Desktop$         

The file is sitting on the desktop at the moment.  Does it need to be anywhere else?

Any other thoughts most welcome.
Cheers,
Col

---

### Post by DerHesse on 2007-01-19
It should stay in the place where it comes from. 
Don't take it anywhere else.

---

### Post by col_b on 2007-01-19
Thanks DerHesse.  I'll leave it on the desktop.  Do you have any idea why it can't open in the first place?  Is there anything I can use to open it other than sh?  

I'm still stuck on this one! ](*,) 

Cheers,
Col

---

### Post by DerHesse on 2007-01-21
did you chmod a+x idv_2_0_linux-i386_installer.sh

before executing?

Or edit the properties of the file within nautilus.

---

