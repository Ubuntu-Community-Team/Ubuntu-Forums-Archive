---
title: "ubuntu 15.10 and netflix"
date: 2017-06-17
forum: General Help
---

### Post by ghostrider0072 on 2017-06-17
hello, anyone know how to watch Netflix on Ubuntu 15.10 ?

---

### Post by coffeecat on 2017-06-17
Ubuntu 15.10 went end of life in July of last year. That means no bug-fixes, no security updates. It's very inadvisable to use an obsolete operating system.

Use the current LTS (long-term support) version 16.04 or, if you want the latest, use 17.04, but 17.04 is only supported until January next year. 16.04 will be supported until 2021.

And to answer your question: install Chrome browser. Netflix just works in Chrome. Not the repository Chromium, but Chrome, which you can download here: [https://www.google.com/chrome/browser/desktop/index.html](https://www.google.com/chrome/browser/desktop/index.html)

---

### Post by efflandt on 2017-06-17
At one time Netflix required Microsoft Silverlight, which in Linux worked with a ppa package that included wine to emulate Windows, gecko (one of many mozilla browsers) to emulate IE, and real MS Silverlight. But that is no longer necessary.

Since Netflix enabled HTML5 it has worked with Google Chrome (64-bit only now), and more recently it works with firefox. But since 15.10 has been obsolete for awhile, I would not know if it works in that. Long term support (LTS) versions of Ubuntu are even numbers ending .04, like 14.04, 16.04, and next will be 18.04. Other shorter term versions are to test changes and possibly support newer hardware.

---

