---
title: "Firefox help - installation"
date: 2005-08-07
forum: General Help
---

### Post by axetickle on 2005-08-07
OK, I have just installed Ubuntu Hoary Hedgehog with no problems... Got my network sorted and configured... no problems.

Now, I already have firefox 1.0.2 pre-installed - it installed itself when I installed Ubuntu.

But I want version 1.0.6 - the only thing is, I have no idea where to install it (I am totally new to linux)... Somebody help?

All/any help appreciated,
Many thanks.

---

### Post by roland on 2005-08-07
[QUOTE=axetickle]OK, I have just installed Ubuntu Hoary Hedgehog with no problems... Got my network sorted and configured... no problems.

Now, I already have firefox 1.0.2 pre-installed - it installed itself when I installed Ubuntu.

But I want version 1.0.6 - the only thing is, I have no idea where to install it (I am totally new to linux)... Somebody help?

All/any help appreciated,
Many thanks.[/QUOTE]

In the main GNOME menu in a section called System Administration (I believe it is called that way), there is a program "synaptic". Synaptic is the Ubuntu package manager, and since all applications are installed with packages, you need to use that. Start Synaptic, and on the left you will see all categories of programs, installed on your computer. On the lower left you can see a number of buttons, "Status" is one of them. Click that one, and you can see which applications are installed, not installed, and -- important -- installed but upgradeable. Click that section, and see if there are any programs to be upgraded. Firefox should be there. Click "Mark all upgrades" on top of the screen, and then "Apply". Now all updates should be downloaded, installed and configured.

If I'm wrong on menu, application and/or button names, please correct me.

---

### Post by axetickle on 2005-08-07
[QUOTE=roland]In the main GNOME menu in a section called System Administration (I believe it is called that way), there is a program "synaptic". Synaptic is the Ubuntu package manager, and since all applications are installed with packages, you need to use that. Start Synaptic, and on the left you will see all categories of programs, installed on your computer. On the lower left you can see a number of buttons, "Status" is one of them. Click that one, and you can see which applications are installed, not installed, and -- important -- installed but upgradeable. Click that section, and see if there are any programs to be upgraded. Firefox should be there. Click "Mark all upgrades" on top of the screen, and then "Apply". Now all updates should be downloaded, installed and configured.

If I'm wrong on menu, application and/or button names, please correct me.[/QUOTE]


Hmm, your help is much appreciated, really. However, I followed all of your instructions to the letter, and have concluded that Firefox is not upgradeable, I'm using version 1.0.2, and when I go to the Firefox website the latest versionis 1.0.6, is this correct?

Also, in your reply, you said that when you click the "Status" button, there will be a section for 'installed but upgradeable' programs, this section was not listed, only Installed and Not Installed were listed. However, when you click "Custom", there is a section called "Upgradeable (upstream)", is this what you intended to mention? If so, Firefox is not listed.  ](*,) 

Any more ideas? Unless it is already at the latest version? But then how do you explain Mozillas 1.0.6 version on their website? Hmmm....


Many thanks.

---

### Post by krusbjorn on 2005-08-07
Open a terminal and type "sudo apt-get update" to update your package database information, and then "sudo apt-get dist-upgrade" to upgrade all your packages that are not up to date.

---

### Post by axetickle on 2005-08-08
Ok, did that, and received this...

> root@ubuntu-laptop:/home/***** # sudo apt-get update
Reading package lists... Done
root@ubuntu-laptop:/home/***** # sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have put asterisks to blank out my name for privacy issues.
I take it this means that everything is up-to-date, which doesn't explain the difference in version numbers as mentioned above. Anybody know why?

Many thanks!  :)

---

### Post by Zifnab on 2005-08-08
[QUOTE=axetickle]
Any more ideas? Unless it is already at the latest version? But then how do you explain Mozillas 1.0.6 version on their website? Hmmm....
[/QUOTE]Packages that work perfectly with Ubuntu aren't magically created each time a piece of software gets an update. ;-)
Every time Mozilla releases a new Firefox version, the good people at Ubuntu/Debian need to manually make a package for you to install. So unless you compile everything for yourself, you won't be on the absolute cutting edge.

---

### Post by roland on 2005-08-08
[QUOTE=axetickle]Hmm, your help is much appreciated, really. However, I followed all of your instructions to the letter, and have concluded that Firefox is not upgradeable, I'm using version 1.0.2, and when I go to the Firefox website the latest versionis 1.0.6, is this correct?

[...]

Any more ideas? Unless it is already at the latest version? But then how do you explain Mozillas 1.0.6 version on their website? Hmmm....

Many thanks.[/QUOTE]

The newest version created by the Ubuntu Team is 1.0.6 indeed, I am actually using it right now. The thing you need to do is clicking the "Reload" button in Synaptic. The newest package info will be downloaded, and Firefox *should* appear in the list. You can check it by searching for "mozilla-firefox", using the search button on top of the screen. The latest version should be "1.0.6-0ubuntu0.1". If you see that, you can upgrade all upgradeable packages by clicking "Mark All Upgrades" and then "Apply".

---

### Post by axetickle on 2005-08-09
Ok guys... appreciate all the help - but a very nice guy in the IRC channel helped me out....

Turns out I didn't have any repositories in my /etc/apt/sources.list file, they were all commented out, and even then, I didn't have the backports.

You'll be happy to know I'm now cruising the internet with my shiny new Firefox version 1.0.6  \\:D/ 

Thank you so much guys!  :smile:

---

