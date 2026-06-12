---
title: "AddPrinter wizard cannot see network printer"
date: 2008-02-21
forum: General Help
---

### Post by eyal p on 2008-02-21
Hello all, I have this problem and I saw quite a few with the same problem as well - but no actual solution. 
Here are the details:
Kubuntu 7.10 on HP laptop. Samba working OK - I can see the HOME net and read and write on the home PC which has XP SP2.
When I try to install a new network printer though, I reach a point where after scanning the net, I can see the computer with the printer, but when I click on it to see the printer I get an error message:
"Error returning browse list: NT_STATUS_ACCESS_DENIED".
The printer is shared and another laptop with XP can print on it.
In addition, when I run" sudo smbtree "  command I can see the printer!
Please, this keeps sleep from my eyes for quite some time now...

---

### Post by erginemr on 2008-02-21
Will this page help?
[http://www.kdedevelopers.org/node/2126/](http://www.kdedevelopers.org/node/2126/)

---

### Post by eyal p on 2008-02-22
Thanks for the link.
I already tried this direction but to no avail.
The system does not see the network printer so I tried manually.
I got stuck with the "Device URI" definition. Could you please clarify what this definition is and how to obtain its values? I am not sure about the hostname  required. 
The smbtree gives me this:

        \\HOME-6B0334EFD4               HOME
                \\HOME-6B0334EFD4\printer               HP Photosmart C3100 series

Thanks!

---

### Post by eyal p on 2008-02-24
i am happy to announce the problem is solved!
The way around was suggested in one of the HP Linux help sites:
I installed gnome-cups-manager, and lo and behold! The printer was detected and installed properly!
I only had to look for the proper driver, and now my system prints OK.

---

