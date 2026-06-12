---
title: "Installing software in Lubuntu? PolKit Error?"
date: 2015-03-04
forum: General Help
---

### Post by TheRealJimShady on 2015-03-04
Hi there,

I have a virtual machine running which I access using remote desktop. It seems to run ok. I first installed Ubuntu 14, and then then when I found that I could not access the 3D Desktop using XRDP, I installed lubuntu desktop. So I now have a xsession file in my home folder which contains the command 'xfce4-session'. So that is my background. What I would like to do now is install RStudio.

1) I download the .deb file here: [http://www.rstudio.com/products/rstudio/download/](http://www.rstudio.com/products/rstudio/download/)
2) It opens in Ubuntu Software Centre, and I click intsall
3) It tries to install, but fails. The errors I get seem to be to do with polkit? They are below:

> 
Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.88'}): org.debian.apt.install-file

Which is then followed by:

> You are not allowed to perform this action. org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name': ':1.88'}): org.debian.apt.install-file

Would love some help please. :-)

Thanks

James

---

### Post by dino99 on 2015-03-04
might help: [http://www.thertrader.com/2014/09/22/installing-rrstudio-on-ubuntu-14-04/](http://www.thertrader.com/2014/09/22/installing-rrstudio-on-ubuntu-14-04/)

---

### Post by TheRealJimShady on 2015-03-04
Thanks, but no, doesn't help.

The problem is more to do with the polkit stuff I think...

---

### Post by grahammechanical on 2015-03-04
Please keep in mind that I am running Ubuntu and cannot speak from experience with Lubuntu but in a matter like this I guess things are the same for Lubuntu as Ubuntu.

To put it simply PolicyKit (PolKit) is a set of files that control how certain utilities work. For example, org.debian.apt.policy will have rules forcing apt to ask for user authenication for the installation of certain software. We can find these policies at /usr/share/polkit-1/actions. 

I do not know the solution to your problem but it seems that the rules are not covering this software. Software Centre will also use this debian.apt.policy rules. That is why it will ask us to authenticate the installation of certain software. You could try installing this software through the terminal using the sudo prefix.

Regards.

---

### Post by TheRealJimShady on 2015-03-04
Thanks for the suggestions and explanation Graham. When I try I get this:

> james@AnalysisUbuntuDesk01:~$ sudo dpkg -i rstudio-0.98.1062-amd64.deb 
[sudo] password for james: 
Selecting previously unselected package rstudio.
(Reading database ... 607786 files and directories currently installed.)
Preparing to unpack rstudio-0.98.1062-amd64.deb ...
Unpacking rstudio (0.98.1062) ...
dpkg: dependency problems prevent configuration of rstudio:
 rstudio depends on libjpeg62; however:
  Package libjpeg62 is not installed.

dpkg: error processing package rstudio (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Errors were encountered while processing:
 rstudio



So I did 'sudo apt-get install libjpeg62' and  then tried again. It seemed to install. But when I click on the RStudio icon in the menu, nothing happens.

---

