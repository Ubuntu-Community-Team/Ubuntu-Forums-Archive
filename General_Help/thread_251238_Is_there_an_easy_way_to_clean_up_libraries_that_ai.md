---
title: "Is there an easy way to clean up libraries that ain't needed anymore?"
date: 2006-09-05
forum: General Help
---

### Post by rejser on 2006-09-05
After a while by installing apps, removing them I guess there are a bunch of libraries and packages that ain't being used by anything (why don't synaptic use aptitude instead of apt-get?).
Is there any smooth way to clean out all of these packages?

---

### Post by elettronicha on 2006-09-05
Yes, there is. Install deborphan and then from the command line run the command "deborphan". It will show you all the orphan libraries, which you will remove/purge as you want with aptitute/apt-get/synaptic. ;)

---

### Post by aysiu on 2006-09-05
If you prefer a graphical interface, use *gtkorphan*.

---

### Post by rejser on 2006-09-06
Thanks, excellent program

---

### Post by Anduu on 2006-09-06
Be careful what you remove however because it isn't foolproof.I Installed a program once that had a certain depedemcy which I had to download from somewhere and GTKOrphan wanted to remove it on me because the dependency didn't link back to the original program.

Now whenever I install something new I emmediately run GTKOrphan to see if anything pops up and fix it.

When you uninstall stuff you are safe to give GTKOrphan free reign.

---

### Post by wieman01 on 2006-09-06
Excellent thread, guys. Thanks. I will check it out as well. have been looking for such a tool for a while.

---

