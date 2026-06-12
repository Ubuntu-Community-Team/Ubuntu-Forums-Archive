---
title: "Running executable using rc.local: does not run on boot up"
date: 2015-04-21
forum: General Help
---

### Post by carr3 on 2015-04-21
Hi,

I am trying to run an executable that starts on boot up.  I have modified the /etc/rc.local file to run the executable located in the /usr/local/bin.  I tested the rc.local script with the command: sudo /etc/init.d/rc.local start, and the executable ran fine.  However, when I restart my system, the application does not run.  I am not sure of the source of the problem because there are no errors or feedback.  Any suggestions would be appreciated.

Thanks,
Carr

---

### Post by pqwoerituytrueiwoq on 2015-04-21
use the full path to the executable file in rc.local

---

### Post by matt_symes on 2015-04-21
Hi

> **carr3 said:**
> Hi,

I am trying to run an executable that starts on boot up.  I have modified the /etc/rc.local file to run the executable located in the /usr/local/bin.  I tested the rc.local script with the command: sudo /etc/init.d/rc.local start, and the executable ran fine.  However, when I restart my system, the application does not run.  I am not sure of the source of the problem because there are no errors or feedback.  Any suggestions would be appreciated.

Thanks,
Carr

Depending on the executable, rc.local may not be the best place to put it.

What is the executable and what does it do ?

Kind regards

---

### Post by carr3 on 2015-04-21
Solved the problem.  Had to use explicit path.  Thanks for your suggestion though!

---

