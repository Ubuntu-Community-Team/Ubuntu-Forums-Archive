---
title: "Help"
date: 2007-01-28
forum: General Help
---

### Post by john38242 on 2007-01-28
Does anyone know how to fix this 


E: Type '/etc/apt/sources.list' is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by meng on 2007-01-28
Show us the output of:
cat /etc/apt/sources.list

(there is some error in that file you need to correct)

---

### Post by john38242 on 2007-01-28
Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.


thats what it says when I try to open add remove programs

---

### Post by johnc4510 on 2007-01-28
Go to this page to get a correct sources.list and how to imput it into the file and update your system: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
This should take care of the problem. NOTE: Choose the correct package list for your flavor of Ubuntu.

---

### Post by meng on 2007-01-28
Or else, please type the command I quoted into a terminal and we should be able to work out how to fix the problem pretty quickly.
> **meng said:**
> Show us the output of:
cat /etc/apt/sources.list

(there is some error in that file you need to correct)

---

