---
title: "Apt-get and clean uninstall"
date: 2005-05-06
forum: General Help
---

### Post by DarkGreen16 on 2005-05-06
I like to have only the things I need on my computer and nothing else..which is one of the reasons I left windows. Almost every single time you uninstall something garbage gets left in the registry. 

I recently install gdesklets and I noticed it installed about 4 dependencies along with gdesklets. I really don't need those extra packages anymore cuz i uninstalled gdesklets. However, when I do a sudo apt-get remove gdesklets it only removes the 1 gdesklets package...is there anyway I can find out what those other packages were and remove them?

thx in advance

---

### Post by Xian on 2005-05-06
[QUOTE=DarkGreen16]However, when I do a sudo apt-get remove gdesklets it only removes the 1 gdesklets package...is there anyway I can find out what those other packages were and remove them?[/QUOTE]
Right-click on the package name in Synaptic and choose 'Properties'.
Then look under the 'Dependencies' tab.

---

### Post by DarkGreen16 on 2005-05-06
thx for the reply but doesn't that list ALL dependencies of that particular program...including ones that might have already been installed by other programs prior to install gdesklets?

I just want to uninstall the dependences for gdesklets and gdesklets only...

i.e. libraries/files used by gdesklets and gdesklets only.

I was thinking maybe an apt-get log maybe?

---

### Post by topcop on 2005-05-06
try using deborphan, its not perfect but its better than nothing.

apt-get install deborphan

---

