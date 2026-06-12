---
title: "plz help, java problem"
date: 2008-05-20
forum: General Help
---

### Post by 1omgz on 2008-05-20
ok heres what happen

I installed java runtime environment - rpm.

i converted the -rpm to a .deb

i installed it..

it worked fine for a day.

ALL java apps worked for one day.

than the next day it just didnt work anymore and it says that i have to install the java plugin.

so i even re-installed it...

And no, it doesnt work.

Im running _Ubuntu 6.06_ and i need help getting my java running again. thanks.

---

### Post by snowbug on 2008-05-20
What I usually do is:
- Go to java.sun.com and download the JRE or JDK for linux directly
- Run the downloaded bin to extract the JRE or JDK
- mv the extracted JRE or JDK to the dir where I'd like to keep it (such as /usr/local/java), then update the /etc/bash.bashrc to export the JAVA_HOME env variable
- Optionally create symbolic link from /usr/bin/java to the actual java executable

That's about it. This way I manage exact Java version I need, and I have mutliple version of it.

However, you mentioned "plugin", which makes me think you are dealing with running Java applet inside browser. Not sure how to do it but I remember for firefox, if you go to its plugin section, there is link for Java Runtime.

---

### Post by 1omgz on 2008-05-20
well specifically, im trying to run a web based game - runescape

---

