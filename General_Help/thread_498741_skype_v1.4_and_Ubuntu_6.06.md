---
title: "skype v1.4 and Ubuntu 6.06"
date: 2007-07-11
forum: General Help
---

### Post by beachreader on 2007-07-11
I recently made the mistake of trying to upgrade from skype1.3 to v1.4. Unfortnately ubuntu 6.06  is missing certain dependencies libasounds2?. It was suggested I install ALSA 1.0.11  and that would solve the issue. From what I read ALSA 1.0.11  can not be installed ubuntu6.06lts. 

Unfortunately I deleted skype v1.3 from my hard drive because I thought perhaps that was creating problems with v1.4. Skype has so far refused to provide me a download verison of    v1.3.

If skype had posted v1.4 will not work with ubuntu 6.06 then I would not have this problem.

typical with new software rollouts it states clearly which OS are needed. i.e. will not work with win 98 ; you need win xp etc.

has any one out there had any luck installing skype v1.4  via ubuntu6.06. I appreciate your help. At this point I will not change my current OS. 

thanks very much. MM :(

---

### Post by AmyRose on 2007-07-11
So you're saying the package is depending on a package newer than what your repos have?

Honestly, I recommend upgrading to Feisty if you can.

---

### Post by andb on 2007-07-14
If you want to go back to 1.3:
If you installed the .deb, sudo dpkg -r skype
then add the skype repository to your sources list:
1. sudo nano /etc/apt/sources.list
2. at the end, add the line:  deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
3. while still in the command line, sudo aptitude update.

Once you have the proper skype repository set up, Id suggest using Synaptic. Find the skype package, then from the menu, choose Package>Force Version, choose 1.3, then Package > Lock version.

This should install 1.3 for you again, and not offer to upgrade.

by the way, instead of saying what OS is needed, they state what DEPENDENCIES there are. Because a Linux OS is not a locked platform like windows, no one knows which version of python or gcc you have on your machine... If possible, its always best (easiest) to use the repositories and aptitude (or apt-get) to install.

---

### Post by mikewhatever on 2007-07-14
If the above suggested does not work, let me know. I'll upload the deb for you.

---

