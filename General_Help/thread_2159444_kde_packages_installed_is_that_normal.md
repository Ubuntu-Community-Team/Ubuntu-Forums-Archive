---
title: "kde packages installed is that normal?"
date: 2013-07-03
forum: General Help
---

### Post by khaos1 on 2013-07-03
Hi guys
I am using 13.04 after an upgrade of 12.10. I have found that many kde packages are installed on my system. The list of kde packages: [http://paste.ubuntu.com/5839868/](http://paste.ubuntu.com/5839868/)
Is that normal? 

Because  I use unity and I don't have installed kde before. I was thinking that maybe is from some dependencies or kde-libs to a program but I can't find out.
Is it safe to remove them? or to check if there are needed to other installed software?

Thanks in advance

---

### Post by mastablasta on 2013-07-03
if you have any KDE programme installed they will be there.

i have Gnome and KDE on windows besides the windows libraries. i have some Gnome and KDE apps on windows. nothing to worry about.

---

### Post by khaos1 on 2013-07-03
Thank you for your reply. Is there a way to findout if these packages are dependencies of a kde app?
Also I found that nepomuk and akonadi is installed and I think that these are not kde-libs but kde-apps and I have never installed them.... strange

Thanks in advance

---

### Post by mastablasta on 2013-07-03
i think synaptic is a good gui package manager that will show you dependecies. it might not look as nice as software center but does the job well.: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
right click the package-> properties -> dependencies tab

also dpkg command can provide plenty of info: [http://www.howtogeek.com/howto/linux/show-the-list-of-installed-packages-on-ubuntu-or-debian/](http://www.howtogeek.com/howto/linux/show-the-list-of-installed-packages-on-ubuntu-or-debian/)
as well as apt-get: [http://askubuntu.com/questions/13296/how-do-i-find-the-reverse-dependency-of-a-package](http://askubuntu.com/questions/13296/how-do-i-find-the-reverse-dependency-of-a-package)

---

