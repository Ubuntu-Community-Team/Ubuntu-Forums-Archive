---
title: "Updating  to Pidgin 4.2.3."
date: 2008-07-09
forum: General Help
---

### Post by iskivgs on 2008-07-09
I'm having trouble updating pidgin. I get about as far as dwnloading the source and after that I'm clueless as to where to go.

---

### Post by unabatedshagie on 2008-07-09
I must have missed a few versons :) last I heard it was 2.4.3 :D

Open up settings > administration > software sources click on the third party software tab and click on the add button.

Paste the following in ```
deb http://ppa.launchpad.net/pidgin-developers/ubuntu hardy main
``` ok it then close the software sources dialog.

Click on reload then you should be able to open the update manager and pidgin should be one of the available updates.

---

### Post by iskivgs on 2008-07-09
Ha my mistake, must be the dyselxia kikin it lol.

Alright well that did the job for the most part now it actually shows 2.4.3 as the latest version. I'm just having some problems updating it now. I tried upgrading it in synaptic pkg mgr but i received an error stating: "the following packages have unresolvable dependencies, make sure all required repositories are enabled". Then it lists this: pidgin:

  Depends: libcairo2 (>=1.6.0) but 1.4.10-1ubuntu4.4 is to be installed
  Depends: libglib2.0-0 (>=2.16.0) but 2.14.1-1ubuntu1 is to be installed
 Depends: liblaunchpad-integration1 (>=0.1.17) but it is not installable
  Depends: libpango1.0-0 (>=1.20.1) but 1.18.3-0ubuntu1 is to be installed
 Depends: libpurple0 but it is not going to be installed
  Depends: perl (>=5.8.8-12) but 5.8.8-7ubuntu3.1 is to be installed

I tried removing it and installing it again but i just get the same error except when trying to install pidgin.

---

### Post by conscious on 2008-07-10
Judging by the versions of libraries you have, you're running Gutsy. It should not be possible to install Pidgin 2.4.3. Generally, you can not install new versions of software for old versions of Ubuntu because they require newer versions of libraries. [Backported versions]("https://help.ubuntu.com/community/UbuntuBackports") are exception.

---

### Post by iskivgs on 2008-07-10
Alright well (running gutsy) i removed it and forced install of 2.2.1 but it says I have broken pkgs. How do I remove or solve this?

---

### Post by Pooka2132 on 2008-07-12
thank you. I didnt have time to check and see how to fix this yet. It worked like a charm for my 8.04.

---

