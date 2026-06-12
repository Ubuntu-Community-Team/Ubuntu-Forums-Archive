---
title: "Broken software installation"
date: 2014-10-19
forum: General Help
---

### Post by ebn on 2014-10-19
Dear sir, 
Whenever I go to ubuntu software center and try to download anything ,I get an error message that " you have two broken packages in your system", I  copy and paste the error message here.
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f


The following packages have unmet dependencies:

avidemux: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is installed
          Depends: avidemux-common but it is not installed
avidemux-qt: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is installed
             Depends: libqt4-opengl (>= 4:4.6.1) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is installed
             Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is installed
             Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is installed
             Depends: avidemux-common but it is not installed
   

Please help me to download softwares , I am using ubuntu 14.04

---

### Post by Impavidus on 2014-10-19
The versions listed as installed are the versions from the default repositories, so I guess they're not from third party sources. Still, do you use third party sources, like PPAs and separate .deb files? And have you run the command```
sudo apt-get install -f
```as suggested? If so, did it work? And if it didn't work, what was the output? Note you have to close the software centre before running that command.

---

### Post by ian-weisser on 2014-10-19
It's not a download problem.
You have a software conflict somewhere.
You must locate and resolve the conflict, or your package manager will remain broken.

How to locate the problem:
Using a terminal, try to install any _one_ of these packages that cannot be installed:
> avidemux: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is installed
          Depends: avidemux-common but it is not installed
avidemux-qt: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is installed
             Depends: libqt4-opengl (>= 4:4.6.1) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is installed
             Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is installed
             Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is installed
             Depends: avidemux-common but it is not installed

Don't try to install all of them. Just one. I would recommend trying to install avidemux_common.
Please show us the entire output, including all those error messages you didn't understand.
We'll help you to understand the problem.

---

### Post by ebn on 2014-10-21
Sir,
 when I try to install-avidemix common through synaptic package manager it shows the followin g error message

E: /var/cache/apt/archives/avidemux-common_1%3a2.5.4-0ubuntu14_all.deb: trying to overwrite '/usr/share/locale/el/LC_MESSAGES/avidemux.mo', which is also in package avidemux2.6-gtk 2.6.8-1~ppa+trusty0

---

### Post by ian-weisser on 2014-10-21
Well, that's not the entire terminal output. When troubleshooting, it helps to use the terminal so you get all the warning and error messages.
But it did identify one problem.

An overwrite error means that two packages are trying to provide the same file. That's not permitted. One file can be supplied by one package. If two packages try to provide the same file, they *conflict*, and the system will stop and raise an error.

Here's what that error message means:
1) You installed avidemux from a PPA some time in the past, and it's still installed.
2) The PPA version conflicts with the Ubuntu Repository Version. You can't have both. You must decide between them.

This happens with PPA and other non-Ubuntu software on occasion.
If you use non-Ubuntu software, you're going to learn how to fix problems like this.

What you can do about it:

- Uninstall all packages from that PPA. Including avidemux and all dependencies. (sudo apt-get autoremove avidemux)
- Disable the PPA. (System Settings --> Software & Updates --> Other Software)
- Refresh your package database. (sudo apt-get update)
- Install avidemux from the Ubuntu Repositories (sudo apt-get install avidemux)

---

### Post by ebn on 2014-10-21
Thank you sir, I can solve my problem

---

### Post by ian-weisser on 2014-10-22
Wonderful!

---

