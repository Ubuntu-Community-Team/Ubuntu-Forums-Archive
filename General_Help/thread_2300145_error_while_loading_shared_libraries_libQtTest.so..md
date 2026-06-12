---
title: "error while loading shared libraries: libQtTest.so.4"
date: 2015-10-23
forum: General Help
---

### Post by francesco29 on 2015-10-23
Hi, I am on Lubuntu 15.10 AMD64. I have installed Mendeleydesktop but when I tray to launch it from the menu nothing happens. When I try within the terminal I get the following message: "mendeleydesktop: error while loading shared libraries: libQtTest.so.4: cannot open shared object file: No such file or directory"
Can anyone help please?

---

### Post by lisette2 on 2015-10-29
Hi Francesco and everyone. I am experiencing exactly the same trouble under linux debian jessie. Any help will be much appreciated.

Bit more of information:
It was actually running neatly for several weeks. Two days ago I think I did an apt-get update and after that, Mendeley would not launch anymore, giving the error message that Francesco already posted, in the terminal.

---

### Post by lisette2 on 2015-10-29
Hi Francesco and everyone. I am experiencing exactly the same trouble  under linux debian jessie. Any help will be much appreciated.

Bit more of information:
It  was actually running neatly for several weeks. Two days ago I think I  did an apt-get update and after that, Mendeley would not launch anymore,  giving the error message that Francesco already posted, in the  terminal.

---

### Post by SeijiSensei on 2015-10-29
It appears to be in the [**libqt4-test**](http://packages.ubuntu.com/trusty/amd64/libqt4-test/filelist) package.  Try installing that.

---

### Post by lisette2 on 2015-10-29
Thank you VERY much. It is running again. For next time: would you hint me on how to figure out which package is missing? I tried to check for the packages, but without success.

---

### Post by SeijiSensei on 2015-10-29
I just did a [Google search]("https://www.google.com/search?q=libQtTest.so.4+ubuntu&ie=utf-8&oe=utf-8") for "libQtTest.so.4 ubuntu".  The second entry pointed to a page at packages.ubuntu.com where all the relevant information is kept.

---

