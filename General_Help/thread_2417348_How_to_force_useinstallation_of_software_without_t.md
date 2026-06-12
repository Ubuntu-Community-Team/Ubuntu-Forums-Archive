---
title: "How to force use/installation of software without the correct Release file."
date: 2019-04-22
forum: General Help
---

### Post by bored-hero on 2019-04-22
I am trying to install the deepin theme, available at ppa:leaeasy/dde. However, because 19.04 is new, the maintainer has not yet added a release file for disco. As a result, running sudo-apt-get update gives me the following output:

[HR][/HR]Ign:7 [http://ppa.launchpad.net/leaeasy/dde/ubuntu](http://ppa.launchpad.net/leaeasy/dde/ubuntu) disco InRelease
Err:8 [http://ppa.launchpad.net/leaeasy/dde/ubuntu](http://ppa.launchpad.net/leaeasy/dde/ubuntu) disco Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/leaeasy/dde/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

[HR][/HR]I am aware that brute forcing software not designed for my OS could cause issues, but I accept this risk and want to throw absolutely all caution to the wind and find a way to force it to use an older Release file. I am aware I could manually download the deb files or build from source, but I want to be able to get updates automatically as the repo is updated, rather than have to go back and reinstall from source or .deb packages every time. 

Is it possible to force sudo apt-get update commands to work with an older Release file in a repo than the version of ubuntu I am currently on? If so, how? Please Advise.

---

### Post by bored-hero on 2019-04-22
Edit: Just realized I posted this in the wrong section of the forum.

---

### Post by bored-hero on 2019-04-22
I am trying to install the deepin theme, available at ppa:leaeasy/dde.  However, because 19.04 is new, the maintainer has not yet added a  release file for disco. As a result, running sudo-apt-get update gives  me the following output:

[HR][/HR]Ign:7 [http://ppa.launchpad.net/leaeasy/dde/ubuntu](http://ppa.launchpad.net/leaeasy/dde/ubuntu) disco InRelease
Err:8 [http://ppa.launchpad.net/leaeasy/dde/ubuntu](http://ppa.launchpad.net/leaeasy/dde/ubuntu) disco Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/leaeasy/dde/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

[HR][/HR]I am aware that brute forcing software not designed for my OS could  cause issues, but I accept this risk and want to throw absolutely all  caution to the wind and find a way to force it to use an older Release  file. I am aware I could manually download the deb files or build from  source, but I want to be able to get updates automatically as the repo  is updated, rather than have to go back and reinstall from source or  .deb packages every time. 

Is it possible to force sudo apt-get update commands to work with an  older Release file in a repo than the version of ubuntu I am currently  on? If so, how? Please Advise.

---

### Post by #&amp;thj^% on 2019-04-22
Knowing the risks you just stated, Change "http://ppa.launchpad.net/leaeasy/dde/ubuntu disco Release"
to:** "http://ppa.launchpad.net/leaeasy/dde/ubuntu/dists/bionic/main Release"**
in your sourcelist.
I still don't see what you will gain from this though, 18.04 is the last Version they have and it was last up-dated 50 weeks ago.
Just install the .deb and be happy. :p

---

### Post by oldos2er on 2019-04-22
Threads merged.

---

