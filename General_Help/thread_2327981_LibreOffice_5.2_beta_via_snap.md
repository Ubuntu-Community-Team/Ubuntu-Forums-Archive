---
title: "LibreOffice 5.2 beta via snap"
date: 2016-06-16
forum: General Help
---

### Post by vasa1 on 2016-06-16
grahammechanical posted about the availability of LibreOffice 5.2 beta (LO5.2) [as a snap package here]("http://ubuntuforums.org/showthread.php?t=2327088&p=13504516#post13504516"). The package has been made by [Bjoern Michaelsen]("https://launchpad.net/~bjoern-michaelsen") and he has blogged about it here: [https://skyfromme.wordpress.com/2016/06/14/libreoffice-5-2-0-beta2-as-a-snap-package/](https://skyfromme.wordpress.com/2016/06/14/libreoffice-5-2-0-beta2-as-a-snap-package/) with complete instructions on how to download and install the package.

I downloaded it and, as mentioned in the other UF link, the download is about 1 GiB. My first concern was whether it would modify my existing profile. So I temporarily renamed *~/.config/libreoffice* to something else.

Then, as per the instructions, I ran */snap/bin/libreoffice* to get LO5.2 going. There were quite a few "messages" in the terminal but the program loaded just fine. I opened a few of my smaller spreadsheets, made changes, and saved under different names. I also played with a few settings and then quit the program. 

the gtk theme used appears to be Adwaita
JRE is installed
[s]no profile was created in my home folder and no changes I made under Tools > Options were saved[/s]
In my home folder I have */home/vasa1/snap/libreoffice/x1/.config/libreoffice/4/user* so that's where snap packages stores user settings. So that means there's no need to protect ~/.config/libreoffice.

At one point, I did something, can't remember what, and the CPU usage shot up to about 60% and stayed there for about a minute.
I noticed that my cursor theme wasn't used which is logical

The work-in-progress release notes for 5.2 are [here]("https://wiki.documentfoundation.org/ReleaseNotes/5.2").

Overall, not a bad experience :)

---

