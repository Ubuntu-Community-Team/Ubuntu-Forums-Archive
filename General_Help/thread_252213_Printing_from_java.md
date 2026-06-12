---
title: "Printing from java"
date: 2006-09-06
forum: General Help
---

### Post by Grymling on 2006-09-06
I upgraded today from Breezy to Dapper.
Everything seems to be ok except for one thing.
Printing from a java application.

In Breezy this was no problem at all.

I have a standard usb-Minolta 1300W and this can't be a printer-problem.
When I try to print the job from my java-application, I get a printer dialog-box, and I can see that my printer has been selected.

So Java can find it. But it says, "not accepting jobs", and thus, nothing comes out of the printer.

This just gotta to be a bug right ?

Outside java the printer works just fine with dapper.

---

### Post by DoctorMO on 2006-09-06
You need to concentrate on understanding what problems may exist between the new version of CUPS (common unix printer system) and the new version of the JVM. perhaps there are known bugs?

other than investigating problems with cups and java will you find your anwser, most people on these fotums won't be able to help.

---

