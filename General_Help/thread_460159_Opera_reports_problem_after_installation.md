---
title: "Opera reports problem after installation"
date: 2007-05-31
forum: General Help
---

### Post by liberalist on 2007-05-31
I downloaded and installed Opera successfully. However, it reported a problem (conflict) when installing the .deb package (for Ubuntu 6.06 LTS).

I downloaded it from: [http://www.opera.com/download/](http://www.opera.com/download/) 

Should I remove Opera? I tried to install it through Synaptic (non-free repository), but this did not work. Thank you very much in advance for your answer.

---

### Post by pak33m on 2007-06-04
What was the conflict exactly? 

If it was a conflict with dependencies you should type the following (at the CLI):

sudo apt-get -f install

Otherwise to install through apt-get perform the following:

Alt+F2 &
Enter gksu gedit /etc/apt/sources.list
Add deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

Then type the following (at the CLI):

sudo apt-get upgrade
sudo apt-get install opera

If you get a conflict with dependencies again type the following (at the CLI):

sudo apt-get -f install

---

### Post by kerry_s on 2007-06-04
You tried adding the repo?-> deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

---

### Post by zvacet on 2007-06-04
Conflict is because in the repos is older version then one you installed.It means nothing,just install version you downloaded.

---

