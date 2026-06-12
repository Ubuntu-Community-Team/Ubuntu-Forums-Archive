---
title: "How to install gnome mines version 3.10.1 in Ubuntu 16.04"
date: 2016-09-02
forum: General Help
---

### Post by van hanegen on 2016-09-02
Hi,
i just need to install previous 14.04 mines in my 16.04 64 bit Ubuntu  alongside or instead of the new mines version. If that is possible, of course. Any advice would be appreciated

---

### Post by howefield on 2016-09-02
Well, not sure I'd recommend it but having tested it, you could download the [package]("http://packages.ubuntu.com/trusty/amd64/gnome-mines/download") from packages.ubuntu.com.

Install with apt.. (assuming downloaded to Downloads folder and is the 64 bit version)

```
sudo apt install ~/Downloads/gnome-mines_3.10.1-0ubuntu1_amd64.deb
```

Then hold the package so the version isn't updated to the xenial package version (3.18.2-2)

```
sudo apt-mark hold gnome-mines
```

---

### Post by van hanegen on 2016-09-02
Many thanks!
But should (and how) i uninstall the xenial version first?

---

### Post by howefield on 2016-09-02
> **van hanegen said:**
> Many thanks!
But should (and how) i uninstall the xenial version first?

```
sudo apt purge gnome-mines
```

---

### Post by van hanegen on 2016-09-02
Yes this exactly what I needed,
**howefield**, thank you so much!

---

### Post by howefield on 2016-09-02
Cool, glad you got what you needed.

---

### Post by Keith_Helms on 2016-09-03
App developers often change things for no apparent reason and I sometimes find I prefer the older version.  For example, gedit used to have fixed size tabs when you had multiple text files open.  With the 16.04 version however many tabs you have open are all sized so they collectively take up the entire width of the screen.  Is that a configurable option?  No.  I prefer the smooth theme tileset in the 14.04 gnome mahjongg to that in the 16.04 mahjongg.  Gnome calculator now has a fixed area above the input field where previous results are displayed.  Can you turn that off?  No.

---

