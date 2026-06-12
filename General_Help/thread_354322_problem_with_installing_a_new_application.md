---
title: "problem with installing a new application"
date: 2007-02-05
forum: General Help
---

### Post by borsel on 2007-02-05
hi,

i am very new to Ubuntu but trying to learn. I am having problem with installing a new application. I am trying to install the application from the "Add/Remove Application" . whatever i try to install from  "Add/Remove Application", i get the same error. The error is "E: graphviz-cairo: subprocess post-removal script returned error exit status 127"  

Can anybody help me with this?

thanx

---

### Post by comfurtn on 2007-02-05
Welcome to Ubuntu!  I've done some research on the error you're receiving... seems to have been common at one time..  to correct the problem,  press alt+f2 which will bring up a run application box.  in it, type:

> gksudo gedit /var/lib/dpkg/status

and press run... you'll have to enter you're password.   In the text file that opens, look for the name of your package (graphviz-cairo).. you can use the find tool to quickly locate it...  immediately beneath the package name should be a line that reads "Status: ..."

CHANGE this line to read:
> 
Package: graphviz-cairo
Status: **purge ok not-installed**

Save the file, and close gedit.  Now try installing your software from Add/Remove again.. hopefully this takes care of your problem..

let me know if it works!

---

