---
title: "Master Pdf Editor  in Ubuntu Mate not working"
date: 2016-07-18
forum: General Help
---

### Post by angelo16 on 2016-07-18
Hi Guys, Does anyone can confirm that Master Pdf Editor 3 in Ubuntu Mate(16.04)  is not working.

When I click on it to run, nothing happens !

Hi Guy, just found that is something related to QT5.2.1

After some googling.... i did 

```
sudo apt-get install qdbus qmlscene qt5-default qt5-qmake qtbase5-dev-tools qtchooser qtdeclarative5-dev xbitmaps xterm libqt5svg5-dev qttools5-dev qtscript5-dev qtdeclarative5-folderlistmodel-plugin qtdeclarative5-controls-plugin -y
```

And now, it runs...

---

### Post by Linuxisfast on 2016-07-18
Get the non qt deb from their site.

---

### Post by stephenbbb on 2016-08-16
there is no non-qt on the site. where did you see that?

---

