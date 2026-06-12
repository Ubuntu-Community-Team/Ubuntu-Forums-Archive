---
title: "Desktop icons with visible rectangle around letters."
date: 2018-06-15
forum: General Help
---

### Post by debderivs on 2018-06-15
Hi,

I´ve installed a new theme to Xubuntu, and it´s added a rectangle to the desktop icons letters.
I saw that some other themes add this too. How can I remove this effect?

Thanks.

Regards.

---

### Post by bodhin2 on 2018-06-15
maybe get a different theme?  possibly theme related

---

### Post by ajgreeny on 2018-06-15
It was possible when using gtk2 themes to get rid of this text background by creating a .gtkrc-2.0 file in your home but so far I have not managed to find a way when using gtk3 themes.

I'm sure there must be other themes than the twop or three default installed ones, that are available and that will not have this problem but I have not bothered to look and now use a vertical, autohidden panel on the left, full of launchers that previously were desktop launchers.

---

### Post by debderivs on 2018-06-16
> **ajgreeny said:**
> It was possible when using gtk2 themes to get rid of this text background by creating a .gtkrc-2.0 file in your home but so far I have not managed to find a way when using gtk3 themes.

I'm sure there must be other themes than the twop or three default installed ones, that are available and that will not have this problem but I have not bothered to look and now use a vertical, autohidden panel on the left, full of launchers that previously were desktop launchers.

Hi,

Thanks for your reply. This theme is Elementary Dark. It´s gtk3, but also gtk2, apparently, because it installs the 
gtk2 folder too, along with unity and metacity. Could the gtk2 interface be selected instead of gtk3? Could try 
that...

Cheers.

---

### Post by debderivs on 2018-06-16
Oh, I forgot to ask something related to this same theme. The greyed out parts of the windows, menus
and submenus, etc. are difficult to see because its font is dark against dark green. Is it possible to
change the font color here? Perhaps a bit lighter font. But where can this be changed? and, will it
affect all windows and menus?

Thanks.

---

### Post by ajgreeny on 2018-06-16
Is the elementary-dark a full theme or an icon theme only?
Can you confirm which version of Xubuntu you are using, as there is a theme configuration utility in 16.04 but not 18.04.

I do not know if it is possible to install the 16.04 gtk-theme-configuration package in 18.04 but it may be worth a try, which I will do shortly on another machine.

---

### Post by ajgreeny on 2018-06-16
I have just had a look in my 18.04 installation and see that gtk-theme-config is already installed so it must be a default package in Xubuntu 18.04 as I did not manually install it.  I thought that it had been removed according to something I read but that was before the version was finally released so it may have been a package of very low priority at that time and thus not yet added to the image.

I have not used it in any version of *ubuntu so can not help any further, but try starting it in terminal of 18.04 with command **gtk-theme-config** or go to **Theme Configuration** in the Settings Manager to see if it does what you want.

---

