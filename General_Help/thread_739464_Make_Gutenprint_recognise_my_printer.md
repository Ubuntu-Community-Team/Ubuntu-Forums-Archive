---
title: "Make Gutenprint recognise my printer"
date: 2008-03-29
forum: General Help
---

### Post by MickS on 2008-03-29
I bought a new printer recently, an HP Deskjet D4260, it was a good price and HPs are supposed to have the best Linux support, got it home and plugged it in up popped a little KDE window saying it recognised the printer and do I want to make it the default printer, I clicked yes and everything worked printing away merrily until I tried to it with the Gimp which just didn't want to know, which is a real shame.
So the question is how do I get Gutenprint to recognise my printer? Or is there another way of printing directly from the Gimp.
I'm running Gutsy Kubuntu and Gimp 2,4,4
Thanks

Mick

---

### Post by DoctorMO on 2008-03-30
Gimp should use the cups system just like everything else, if gimp doesn't work but other programs do then that is a problem for gimp and you should report the problem.

As far as I can see your printer works. In order to print you may have to save your gimp files as png and open them up in the image viewer and print from there.

---

### Post by MickS on 2008-03-30
> **DoctorMO said:**
> 

As far as I can see your printer works. In order to print you may have to save your gimp files as png and open them up in the image viewer and print from there.

That's what I have been doing but it's a shame because I like Gutenprint and it worked perfect with my old printer.

Mick

---

### Post by DoctorMO on 2008-03-31
> That's what I have been doing but it's a shame because I like Gutenprint and it worked perfect with my old printer.

Gutenprint is a driver set, it has _nothing_ to do with gimp other than being a spawn from it. the gutenprint drivers are being used by cups in order to print. If you are selecting the gutenprint driver instead of the hplip driver then that might be your problem, but you should check your printer settings.

Once again, this isn't something to do with gutenprint, but a problem with gimp.

---

