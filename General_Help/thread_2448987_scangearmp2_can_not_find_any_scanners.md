---
title: "scangearmp2 can not find any scanners"
date: 2020-08-17
forum: General Help
---

### Post by raleigh3 on 2020-08-17
I am trying out version 20.04 on a persistent pen drive.

I installed all required drivers for my Canon TS9120 scanner/printer.

But scangearmp2 can not find any scanners.

It worked find with ubuntu-mate 18.04?

---

### Post by Impavidus on 2020-08-18
Have you connected it by usb or via the network? In the latter case, it may require some additional configuration. I haven't got a Canon scanner, so I can't help with the details, but with my network Epson scanner I had to put the IP address in a config file in /etc.

---

### Post by raleigh3 on 2020-08-18
I tried the usb.

What is frustrating is I had no problem when using UM 18.04.

---

### Post by raleigh3 on 2020-08-20
Should I report this as a bug to Launchpad?

There is nothing in /var/crash, but a scanner not working is pretty serious, especially since it worked in previous distros.

---

### Post by deadflowr on 2020-08-20
Where is the package from?
A PPA?
I don't see it as an official package in the repositories.

If a PPA then you'll more likely need to contact the PPA owner directly, 
or if lucky the PPA has a link to where bugs can be reported.

Launchpad doesn't track bugs for PPA like it does for officially included packages in the repos.

---

### Post by raleigh3 on 2020-08-20
What is PPA?

scangearmp2 is part of the drivers for the scanner.

---

### Post by raleigh3 on 2020-08-20
I am trying to think "outside the box." :-)

To use my scanner, I had to leave 18.04 installed while also having 20.04.

Which uses a lot of space and it takes longer for cloning program to make images.

Is there large portions of 18.04 I can eliminate except what is necessary to run my scanner?

---

