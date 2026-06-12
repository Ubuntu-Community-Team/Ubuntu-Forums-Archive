---
title: "Root Access for Antivirus"
date: 2008-05-06
forum: General Help
---

### Post by CharmCityCrab on 2008-05-06
I have installed the AVG free antivirus 7.5 package.  Unfortunately, it will not get updates and is denied access to various folders it tries to scan.

I am assuming the problem is that the program doesn't have root access.  How can I assign just that single program default root access?  Or, if someone knows that that's not the problem, what do I need to do to get it running on all cylinders?

---

### Post by mikewhatever on 2008-05-06
To update use Alt+F2, <sudo avgupdate -o>.
To start AVG as root, use Alt+F2, <sudo avggui>.
I am pretty sure you can also update AVG from GUI while running it as root.

---

