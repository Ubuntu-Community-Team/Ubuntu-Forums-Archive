---
title: "Abnormal Shutdown Screen?"
date: 2012-12-01
forum: General Help
---

### Post by Armissea on 2012-12-01
Why is my shutdown screen showing up like this?

it did this right after I upgraded to 12.10

---

### Post by MyTinFoilHat on 2012-12-01
I second this question. This is how my shutdown appears also. Sometimes mine even says [fail].

---

### Post by 2F4U on 2012-12-01
What is the problem? Your system tells you that it successfully and normally shut down all processes. No process had to be forced to shutdown, so the shutdown was most likely clean.

---

### Post by rnerwein on 2012-12-02
> **2F4U said:**
> What is the problem? Your system tells you that it successfully and normally shut down all processes. No process had to be forced to shutdown, so the shutdown was most likely clean.
in the shutdown procedures there is first a friendly kill ( -15 ) is send to all remaining processes.
but if after a limited time there are some running processes the system is send them
the kiss of death ( meaning kill -9 )
the message you see comes from the kernel and is ok ( i wonder you must be very fast to
get a picture of this screen)
cheers :-)

---

### Post by bhaveshnande on 2012-12-02
> **2F4U said:**
> What is the problem? Your system tells you that it successfully and normally shut down all processes. No process had to be forced to shutdown, so the shutdown was most likely clean.

But shouldn't it show a nice "shutting down.." like windows instead of the kernel messages?

---

### Post by rnerwein on 2012-12-02
> **bhaveshnande said:**
> But shouldn't it show a nice "shutting down.." like windows instead of the kernel messages?
to show a nice picture would be nice but impossible - X on this point is long time gone.
but i wonder - i saw this message only one or two times on 12.04.
but i told you that is no error (may be it is addict from the speed of your box or so)
cheers

---

### Post by 2F4U on 2012-12-02
> **bhaveshnande said:**
> But shouldn't it show a nice "shutting down.." like windows instead of the kernel messages?

This is 
1. a matter of taste. Some people like to visually be assured that their box is cleanly shutting down.
2. up to the developers on how to implement this.
3. a matter of what is technically possible.
4. not Windows.

---

### Post by MyTinFoilHat on 2012-12-03
> **2F4U said:**
> This is 
1. a matter of taste. Some people like to visually be assured that their box is cleanly shutting down.
2. up to the developers on how to implement this.
3. a matter of what is technically possible.
4. not Windows.

(I haven't made it to that chapter yet). Thank you for answering for me, too.

---

