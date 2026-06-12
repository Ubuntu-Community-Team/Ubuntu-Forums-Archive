---
title: "Code::Blocks with QT4 solution - so simple -"
date: 2016-05-15
forum: General Help
---

### Post by David_Ramsay on 2016-05-15
Installed Ubuntu 16.04 LTS from scratch after using 14.04 LTS for years
and thought would re-attack this problem now that I have a clean install.

Code::Blocks QT4 wizard always failed when using the QT4 new project wizard.

Installed Code::Blocks v16.01
Installed libqt4-dev

Checked where libqt4-dev installed to using:-

dpkg --listfiles libqt4-dev

QT4 mainly installed to: /usr/share/qt4/
QT4 libs installed to: /usr/lib/x86_64-linux-gnu/

Then I created a soft-link 'lib' folder inside the folder '/usr/share/qt4'

sudo ln -s /usr/lib/x86_64-linux-gnu /usr/share/qt4/lib

Re-Tried Code::Blocks "create a qt4 project" wizard and it worked
just as simply as other project wizards and the code compiled. 

For QT5, may need a separate wizard I guess - not yet tried.

Would love to know if works for others. :)

---

