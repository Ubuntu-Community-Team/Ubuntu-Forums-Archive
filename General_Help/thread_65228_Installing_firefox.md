---
title: "Installing firefox"
date: 2005-09-13
forum: General Help
---

### Post by mcndjxlefnd on 2005-09-13
I have hoary 5.04 and I've been trying to install firefox, without any success.  I have looked all over the internet, and tried to find the steps to install it, but none of these worked either.  I suspect the problem is with ubuntu.  HOW do I install firefox on Ubuntu? preferably a step by step explanation, with logical reasoning for each step (if I understand why I am moving files around, or entering specific commands, it would help me understand the steps).

---

### Post by heimo on 2005-09-13
You should have firefox installed by default in Ubuntu. But if it's not, you can run this on terminal:
 ```
sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support
```

EDIT: Or you could install same packages using Synaptic Package Manager (System->Administration)

---

### Post by Elrohir on 2005-09-13
thats for installin the ubuntu release of Firefox... if you have downloaded the package from mozilla.org, then unpack (Archive Manager or tar -zxvf <package>), though terminal goto the folder where Firefox is unpacked (assuming it has unpacked on Desktop, cd /home/<user>/Desktop/firefox)... I belive there's an installer... through terminal,  ```
./firefox-installer
``` have fun...

---

### Post by varunus on 2005-09-13
[QUOTE=Elrohir]thats for installin the ubuntu release of Firefox... if you have downloaded the package from mozilla.org, then unpack (Archive Manager or tar -zxvf <package>), though terminal goto the folder where Firefox is unpacked (assuming it has unpacked on Desktop, cd /home/<user>/Desktop/firefox)... I belive there's an installer... through terminal,  ```
./firefox-installer
``` have fun...[/QUOTE]

Why would you want to do this, though?  Ubuntu has the newest firefox (1.06) if you enable backports.

Instructions here, it'll upgrade most of your packages to their newest versions, and enable some others:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by mcndjxlefnd on 2005-09-13
Sorry Guys, none of that advice has helped.  I get error messages like too many dependant files with nothing to be dependant upon.

---

### Post by heimo on 2005-09-13
Could you please include the actual error/warning messages? Maybe it's about your sources.list or some packages not installed /configured properly.

---

### Post by buldir on 2005-09-14
[QUOTE=varunus]Why would you want to do this, though?  Ubuntu has the newest firefox (1.06) if you enable backports.

Instructions here, it'll upgrade most of your packages to their newest versions, and enable some others:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)[/QUOTE]

[This](http://ubuntuforums.org/showthread.php?t=58639) is why.

---

