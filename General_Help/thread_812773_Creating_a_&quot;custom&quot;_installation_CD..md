---
title: "Creating a &quot;custom&quot; installation CD."
date: 2008-05-30
forum: General Help
---

### Post by paulig2001 on 2008-05-30
Hi,

I've created a web based application written in Python and R for analyzing bioinformatics data from DNA microarrays, I would like to freely distribute my work on the net. 

I've built the application in Linux, but the problem with distributing it is that it requires a whole host of stuff to be installed by the end user before the R and Python scripts will run.

I'm wondering if anyone can point me in the right direction of how I'd go about packaging everything on a single installer CD that would install Ubuntu and all the stuff needed to make the application work? Creating a custom Ubuntu distribution of sorts...

There are one or two programs that need to be compiled from source and a number of additional packages need to be added to R and Python, if thats a problem?

Any help in pointing me in the right direction is very much appreciated.

-Paul.

---

### Post by WRDN on 2008-05-30
Couldn't you write scrips to install the other packages?

---

### Post by paulig2001 on 2008-05-30
I guess so, but if I write a script to install all that stuff on top of a default installation, is there a way of altering the installation CD to run this custom script at install time?

---

### Post by bingoUV on 2008-05-30
You have to create an upstart job to run such a script. As the last part of the job, it will delete itself. So that it will run only the first time a user boots, and not everytime. Read about jobs here  : [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

