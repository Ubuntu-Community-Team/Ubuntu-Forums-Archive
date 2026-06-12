---
title: "Error: Broken count &gt;0  after installing skype"
date: 2012-11-16
forum: General Help
---

### Post by swizzla on 2012-11-16
Hi,

I cant figure out how to fix this problem. It started when I tried to install skype. I would get an error after the installation saying Error: Broken count>0 in the system tray, and in the software center there would be a popup saying that the software catalog was broken. It also happens when i try to install wine or anything with a 32bit library. it was happening since i was using 12.04. I upgraded hoping the upgrade would solve the problem but its still here.

so far i've tried several fixes with no success:

sudo apt-get -f install,
sudo apt-get check && sudo apt-get -f install
sudo apt-get autoclean && autoremove

then did the same things using aptitude, which seemed to do more than apt-get and showed a bunch of dependency conflicts

sudo dpkg --configure -a

I reinstalled multiarch and ia32 libs

the only thing that got rid of the errors was to purge skype, wine and anything that wasnt 64-bit.

Can anyone help me figure out where I'm going wrong please? I need to have skype and wine installed but the dependency issues are a real annoyance.

Thanks

---

