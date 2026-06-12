---
title: "Using a download accelerator with apt-get"
date: 2007-10-29
forum: General Help
---

### Post by go_beep_yourself on 2007-10-29
I am trying to follow [this guide]("http://budlite.blogspot.com/2007/08/using-download-accelerator-with-apt-get.html"), but the command

apt-get -y --print-uris package_name > debs.list

does not work.

Can anyone help?

---

### Post by vukko on 2008-01-26
Ya, seems the author left out the <option> bit. It Should be:

apt-get -y --print-uris install package_name > debs.list

---

