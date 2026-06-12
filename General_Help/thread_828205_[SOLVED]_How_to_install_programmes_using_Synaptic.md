---
title: "[SOLVED] How to install programmes using Synaptic"
date: 2008-06-13
forum: General Help
---

### Post by Dyffo on 2008-06-13
I am a complete Newbie - can someone please guide me through the process of installing programmes using Synaptic Package Manager.I am probably stupid but just cannot get to grips with this. My latest problem is trying to update a-Mule to the latest version.I have downloaded taz files, bin files and more but just cannot get to grips. There are loads of situations that I would like to download and install but cannot do these through the Add/remove facility.

---

### Post by prince_niceguy on 2008-06-13
Synaptic can be used to install programs in the repository. For installing programs from tar ball just follow the instruction in the INTALL file of the program that should give you more information on instruction.

For installing program in repository. Open synaptic. Search for you program. Double click the program and click on apply and it will install the program.

---

### Post by NilsE on 2008-06-13
Installing through Synaptic Package Manager is pretty easy

1) Search for the package you want
2) Click on the box next to it and select what you want to do (Install, reinstall, or remove)
3) Click apply

You mentioned downloading packages. In which case, if they are packages that are in the repositories you don't have to do that.  Just use Synaptic.  If they are packages that are not in the repositories you will have to follow the instructions for the package.  The easiest ones are those that are .deb files since that is native to Ubuntu as Ubuntu is debian based and can be installed with either command lines in a terminal or with the deb installer. Actually you can just download them to your desktop and double click on them and the installer will be triggered.

Like I said, others like .rpm and archived packages will take extra actions.

---

### Post by ktechman on 2008-06-13
System/Administration/Synaptic Package Mgr be sure your sofware sources list is up to date check the boxes "Canonical sources" then go to "Third party software" check all boxes then update mgr and see if any are available. then go back to "Synaptic package Mgr" and search for your apps (entries need to be exact in the search window) instead of add and remove also in A"dd and Remove" change the drop down choices to "All available".

Cheers

If this solves your problem, mark this as solved in "Thread Tools" please:)

---

### Post by NikoC on 2008-06-13
Hmmm,

Let me try and clear things up for you. If you would like to install software that is provided via the so called repositories you can use synaptic. Just launch synaptic, search for the program you want to install (e.g. Opera web broswer), right click on the program and choose 'Mark for installation' and then 'Apply'. To remove an installed package you can use the same method, but select removal or complete removal.

If you want to install software that is not available via the repositories (and thus via synaptic) you have to download the package from let's say a certain web location. The easiest way to install such packages is to download the file with the .deb extension. You can just double click such a file to install it (a bit like an .exe file in windows). You also can install other types such as .tar, .bin etc. In such case I would refer the software developer's installation guide.

Hope this helps you out,

Cheers.

edit: as usual already several other responses where posted while I was typign ;)

---

### Post by Kevbert on 2008-06-13
You're trying to install amule P2P software.   
1) Go to System-Preferences-Administration and click on Synaptic Package Manager.
2) Enter your log-in password when prompted.
3) Click on search and enter amule.
4) All search results will be shown.  The latest official version is 2.1.3-3.  Note if you get nothing you will need to go to System-Administration- Software sources and enable all boxes under the Ubuntu Software tab and All updates apart from Proposed (read unstable) under the Updates tab.
4) Left click on the amule box (top one) and select Mark for installation.
5) A new box will be displayed showing you what other files/packages are needed to run amule.  Click on Mark.
6) Now click on the apply icon and everything should install...

---

