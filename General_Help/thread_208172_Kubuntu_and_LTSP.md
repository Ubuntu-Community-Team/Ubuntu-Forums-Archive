---
title: "Kubuntu and LTSP?"
date: 2006-07-03
forum: General Help
---

### Post by v4169sgr on 2006-07-03
[This post is being repositioned for greater exposure as although I am sure server talk is the right forum nevertheless this issue is not getting enough exposure. Original posting is here:

[http://ubuntuforums.org/showthread.php?p=1206776#post1206776](http://ubuntuforums.org/showthread.php?p=1206776#post1206776)

This problem is about getting a functional KDE desktop over the Ubuntu LTSP framework]

My setup is basically Ubuntu with kubuntu-desktop [users prefer KDE] and edubuntu-server package with the ltsp-server and ltsp-standalone packages. I built the server environment using ltsp_build_client, and after many trials and tribulations described elsewhere, finally got a client-server arrangement working.

Where I would like to be:
* Faces theme log in with the nice power switch bottom left [I use GDM with human-list theme to log in to KDE for lack of any other suitable option at this time]
* KDE desktop environment, as similar as possible to the users own environments back on the main machine

What I am getting:
* Really simple GDM theme logging into Gnome [with the nice power switch];
* Messed up application menus [basically because all user use KDE then all apps are at same level under the top level [education,Office,System etc];
* Sound directed through the server [am working on this - less important than the KDE desktop]

I think I messed up, because, having followed the instructions in:

[https://help.ubuntu.com/community/HowToCookEdubuntu/Chapters/LTSPManagement](https://help.ubuntu.com/community/HowToCookEdubuntu/Chapters/LTSPManagement)

[the bit about 'Updating your clients ...']

while in the chroot I then ran "apt-get install kubuntu-desktop" in the hope of delivering the KDE desktop to my clients. 401M of updates later, and I get a system in which the brown Ubuntu boot up sequence is followed, dcop complains it didn't get write priviliges, a KDM log in screen with the default Dapper theme, and users cannot log in - they didn't get authorisation].

QUESTION: How can I get KDE over Dapper LTSP??

Many thanks in advance!:cool:

---

### Post by v4169sgr on 2006-07-03
Your help will be appreciated :D

---

