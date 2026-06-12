---
title: "Ubuntu desktop environment is gone after installing wine"
date: 2013-09-15
forum: General Help
---

### Post by kschlichther on 2013-09-15
Hi, my Ubuntu desktop environment, the GUI in its entirety has dissapeared completely after i installed wine1.5 using the following commands:



sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.5

Chrome is still running fine and most other programs appear to work. I can see my desktop and the icons/folders. However, the entire side menu bar is gone, as well as the top menu bar, and any menu bar that would have been around a window. i.e. a terminal window has the slim black bar that says "Terminal". Does anyone know what packages need to be downgraded to fix whatever i have done?

I am running Ubuntu 12.04LTS

here is a link to my terminal which i managed to copy paste. I do not know which packages have caused this. The only way i can use terminal commands is to go into the shell with ctrl+alt+f1



[http://www.mediafire.com/view/dfausg1wzts23yl/install-wine-terminal](http://www.mediafire.com/view/dfausg1wzts23yl/install-wine-terminal)

EDIT: Issue was solved after uninstalling wine and several other packages, followed by a reboot

---

