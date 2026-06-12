---
title: "timeout &quot;xxx is not responding&quot; is too short"
date: 2022-10-20
forum: General Help
---

### Post by col48 on 2022-10-20
Many actions in my spreadsheets take a long time - tens of seconds - to run and I see the popup message a lot.  I've also seen this a few times with other applications, so it isn't just a LibreOffice issue.

On this gitlab post [https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/2484]("https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/2484") this Terminal command is given to change the timeout to 30 seconds:
```
gsettings set org.gnome.mutter check-alive-timeout 30000
```
The post is for Arch Linux and is 2 years old.

1. Would this work for Ubuntu 22.04 too?
2. If it is done, would the change be permanent - ie survive rebooting?

PS: the gitlab post 's OP reported the program would quit if the timeout popup's Continue button was not pressed quickly.  But that is not so here, seeing the popup so frequently is just annoying, not a show-stopper.

---

### Post by QIII on 2022-10-20
How large are your spreadsheets?  

Are you using any macros?

Have you created macros that run in response to certain user actions?

---

### Post by col48 on 2022-10-20
Spreadsheets can be several tens of thousands of rows (no macros) but what slows down loading, saving, sorting, copy/paste etc is that each row may contain a couple of hundred cells with formulae.

I have one spreadsheet with about 25000 rows and 200 columns (many of the cells are empty) with no formulae and this can be sorted in under one second so I am sure it is the formulae which make the difference.

I don't have an issue with the length of time operations take, but if the setting for the timeout wait time could be changed as easily as by a simple Terminal command I would be very pleased.

---

