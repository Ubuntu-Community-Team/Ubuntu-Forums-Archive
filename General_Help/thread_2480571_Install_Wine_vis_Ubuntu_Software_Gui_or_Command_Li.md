---
title: "Install Wine vis Ubuntu Software Gui or Command Line?"
date: 2022-11-02
forum: General Help
---

### Post by fran_3 on 2022-11-02
The Status:
- I'm running Ubuntu 22.04.1 and have minimum Linux experience.
- I want to install Wine and see if it will install and run Corel Draw X3 as it won't install on Windows 10. (I have the Corel Draw X3 installation CD and I own it)

The Questions: Which is the best way to install Wine?

a - Use the "Ubuntu Software" Icon to search for and install Wine... or

b - Use the Terminal/Command Line as described in this YouTube Video... "How to Run Windows Programs on Linux | Wine Install Tutorial using Ubuntu 20.04 LTS"
...  Which does the following...

- installs the i386 architecture
- downloads the repository key
- adds repository to help install Wine
- installs the Wine Stable Package
- installs PlayOnLinux

Here are the actual terminal commands from the video to do the above...
1. sudo dpkg --add-architecture i386 
2. wget -O - [https://dl.winehq.org/wine-builds/winhq.key](https://dl.winehq.org/wine-builds/winhq.key) | sudo apt-key add -
3. sudo add-apt-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) focal main'
4. sudo apt install --install-recommends winehq-stable
5. sudo apt install playonlinux

In Summary:
Using the "Ubuntu Software" Icon certainly seems simpler but I thought I would ask before proceeding.

Thanks for any help.

PS and what about Q4Wine? What does that do?

---

### Post by Holger_Gehrke on 2022-11-02
According to the [Wine AppDB]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=5321") Corel Draw X3 is a bit of a problem child. The best results (a "gold" rating) where for Ubuntu 18.04 using Wine 3.0.5. Results with later version of Wine and Ubuntu were less then great. If it was me, I'd install PlayOnLinux from the standard repositories and use that to install Wine 3.0.5 (one of the thing POL allows you to do is to have multiple versions of Wine installed and associate programs to a specific Wine version ...) and then follow the various workarounds listed in the AppDB entry.

Q4Wine is a QT-based GUI for wine. If you're using PlayOnLinux Q4Wine is not all that useful.

Holger

---

### Post by aug7744 on 2022-11-02
Install using information from
[https://wiki.winehq.org/Download](https://wiki.winehq.org/Download)
Install the wine-dev version.
After install gecko both 32 and 64 bits and install wine.mono msi file from

[https://github.com/madewokherd/wine-mono/releases](https://github.com/madewokherd/wine-mono/releases)

---

### Post by dragonfly41 on 2022-11-02
Depending on your requirements there are Linux alternatives ..

[https://www.linuxlinks.com/best-free-open-source-alternatives-coreldraw/](https://www.linuxlinks.com/best-free-open-source-alternatives-coreldraw/)

SVG-Edit might help you.
And Inkscape.
Not on the list is BoxySVG available as Ubuntu package, with the others.

---

